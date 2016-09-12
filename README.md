 [![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://raw.githubusercontent.com/angelcs1990/GQImageViewer/master/LICENSE)&nbsp;
[![](https://img.shields.io/badge/platform-iOS-brightgreen.svg)](http://cocoapods.org/?q=GQImageViewer)&nbsp;
[![support](https://img.shields.io/badge/support-iOS6.0%2B-blue.svg)](https://www.apple.com/nl/ios/)&nbsp;
# ImageViewer
一款仿微信多图片及视频浏览器，图片和视频原尺寸显示，不会变形，双击图片放大缩小，单击消失，支持多张本地和网络图片以及网络视频混合查看，支持链式调用。不需要跳转到新的viewcontroller，就可以覆盖当前控制器显示。

## Overview

![Demo Overview](https://github.com/g763007297/GQImageVideoViewer/blob/master/Screenshot/demo.gif)

##CocoaPods

1.在 Podfile 中添加 pod 'GQImageVideoViewer'。
2.执行 pod install 或 pod update。
3.导入 GQImageVideoViewer.h。

## Basic usage

1.将GQImageVideoViewer文件夹加入到工程中。如果你的工程中有SDWebImage就不需要再添加，如果没有则需要将SDWebImage加入。

2.在需要使用的图片查看器的控制器中#import "GQImageVideoViewer.h"。

3.在需要触发查看器的地方添加以下代码:

```objc

//基本调用
[[GQImageVideoViewer sharedInstance] setImageArray:imageArray];//这是图片数组
[GQImageVideoViewer sharedInstance].usePageControl = YES;//设置是否使用pageControl
[GQImageVideoViewer sharedInstance].selectIndex = 5;//设置选中的图片索引
[GQImageVideoViewer sharedInstance].achieveSelectIndex = ^(NSInteger selectIndex){
    NSLog(@"%ld",selectIndex);
};//获取当前选中的图片索引
[GQImageVideoViewer sharedInstance].laucnDirection = GQLaunchDirectionRight;//设置推出方向
[[GQImageVideoViewer sharedInstance] showInView:self.navigationController.view];//显示GQImageViewer到指定view上

//链式调用
[GQImageVideoViewer sharedInstance]
.imageArrayChain(imageArray)
.usePageControlChain(NO)
.selectIndexChain(6)
.achieveSelectIndexChain(^(NSInteger selectIndex){
    NSLog(@"%ld",selectIndex);
})
.launchDirectionChain(GQLaunchDirectionRight)
.showViewChain(demoView);

```

特别说明，如果是下网络图片的话，在iOS9以上的系统需要添加plist字段，否则无法拉取图片:

```objc

<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key>

<true/>

</dict>

``` 

## Level history

(1) 0.0.1

github添加代码

(2) wait a moment

##Support

欢迎指出bug或者需要改善的地方，欢迎提出issues，或者联系qq：763007297， 我会及时的做出回应，觉得好用的话不妨给个star吧，你的每个star是我持续维护的强大动力。
