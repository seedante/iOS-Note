*笔记内容：*

### [Core Data 框架](https://github.com/seedante/Note/wiki/Core-Data):

Core Data 非常复杂，笔记目前总结了以下内容: Stack, Data Type, Relationship。

### [Photos 框架](https://github.com/seedante/iOS-Note/wiki/Photos)

介绍了常用 API 和一些坑。

### [iOS 视图控制器转场(动画)详解](https://github.com/seedante/iOS-Note/wiki/ViewController-Transition)

详尽地解释了全部转场机制，近期也更新了 iOS 10 中新引入的 UIViewPropertyAnimator 部分，同时该类也可用于实现交互动画。
该文也发布在唐巧前辈的「iOSDevTips」公众号。

### [自定义容器控制器转场](https://github.com/seedante/iOS-Note/wiki/Custom-Container-View-Controller-Transition)

iOS 本身并不直接支持自定义容器控制器的转场，我们可以自己添加协议来实现。这个是「转场动画详解」的一部分，由于原文部分太长了，便将这个剥离出来单独成章。

### [视图性能优化：离屏渲染](https://github.com/seedante/iOS-Note/wiki/Mastering-Offscreen-Render)

objccn.io 的译者将 Offscreen Render 译作「离屏渲染」真的是很传神，关于离屏渲染的概述可参考 objccn.io 的译文:[绘制像素到屏幕上](https://objccn.io/issue-3-1/)，通俗易懂。在已公开的官方资料里，最早可追溯到2011年的 WWDC，此后几年的 WWDC 有关视图方面的 session，大多都介绍了如何避免离屏渲染来提升视图性能以及使用工具来检测离屏渲染。

能触发离屏渲染，并且使用不当时会对视图性能造成严重影响的几种效果：阴影 Shadow, 圆角 RoundedCorner，遮罩 Mask。
这其中圆角效果最为广泛使用，今年初涌现了一大波重绘圆角的解决方案，这种方案简单粗暴，但是比较浪费内存，而且不适用于文本视图的圆角效果。实际上除了 Mask，前两种效果都有方法来避免触发离屏渲染，而且实现成本也很低。

离屏渲染本来是一种优化机制，但是上面几种效果触发离屏渲染后会严重影响视图性能，如何利用离屏渲染来改善视图性能？实现方法是极其简单的。

本文针对各种效果的优化都做了对比测试并提供了 Demo。本文也发布在唐巧前辈的「iOSDevTips」公众号。


### [交互式动画](https://github.com/seedante/iOS-Note/wiki/Interactive-Animations)

[ WWDC 2016 Session 216: Advances in UIKit Animations and Transitions ](https://developer.apple.com/videos/play/wwdc2016/216/)介绍了一个非常有意思的类`UIViewPropertyAnimator`，该类让动画与交互无缝连接。
该类有个很好的使用场景：转场动画的交互。之前转场动画的交互有很大的局限：无法随意在动画与交互之间切换，`UIViewPropertyAnimator`消除了这个局限。
iOS 10 在转场协议中引入了`UIViewPropertyAnimator`的相关协议，不过为了向下兼容，使得原本比较复杂的转场协议变得臃肿无比，实际上没有这个必要，我在 [iOS 视图控制器转场(动画)详解](https://github.com/seedante/iOS-Note/wiki/View-Controller-Transition-PartII#Chapter3.7) 介绍了该类带来的交互新特性，以及如何利用该类来精简转场协议。

转场动画中的动画和普通的 UIView Animation 和 Core Animation 并无二致，因此使用`UIViewPropertyAnimator`让普通的动画实现交互也是个很有意思的话题。这里的文章是两篇文章的合集：

1. [交互式动画(上)：iOS 10 以下的实现](http://www.jianshu.com/p/bbbdff8f01c5)
2. [交互式动画(下)：UIViewPropertyAnimator in iOS 10](http://www.jianshu.com/p/6ac70183631e)

这两篇文章也发布在 InfoQ 网站：[上](http://www.infoq.com/cn/articles/ios-interactive-animation-p1?utm_campaign=rightbar_v2&utm_source=infoq&utm_medium=articles_link&utm_content=link_text)和[下](http://www.infoq.com/cn/articles/ios-interactive-animation-p2)。
