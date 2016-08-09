###iOS Project Toolchain

CocoaPods安装：
- [CocoaPods安装和使用教程](http://code4app.com/article/cocoapods-install-usage)
- [iOS项目工作空间搭建](http://www.cnblogs.com/songxing10000/p/4930824.html)
- [Cocoapods配置文件Podfile编写](http://blog.csdn.net/clwahaha/article/details/22193873)
- [设置git/npm/bower/gem镜像或代理方法](https://segmentfault.com/a/1190000002435496)

> 有可能需要设置代理：export http(s)_proxy='http(s)://xxx.com:port'

####Podfile:
```
source 'https://github.com/CocoaPods/Specs.git'

# Uncomment this line to define a global platform for your project
platform :ios, '8.0'
# Uncomment this line if you're using Swift
use_frameworks!

target 'XXXX' do
  pod 'AsyncSwift'
  pod 'Spring', :git => 'https://github.com/MengTo/Spring.git', :branch => 'swift2'
  pod 'Fabric'
  pod 'Crashlytics'
end

target 'XXXXTests' do

end

target 'XXXXUITests' do

end
```

###iOS可持续化集成
- [iOS可持续化集成: Jenkins+bundler+cocoapods+fastlane](http://www.cocoachina.com/ios/20150728/12733.html)
- [iOS continuous delivery with Jenkins and Fastlane](https://labs.kunstmaan.be/blog/ios-continuous-delivery-with-jenkins-and-fastlane)
- [CI server on Mac OS for iOS using GitLab and Fastlane](http://indeema.com/blog/ci-server-on-mac-os-for-ios-using-gitlab-and-fastlane)

###iOS-OpenGLES工程搭建
- [iOS使用Workspace来管理多项目](http://blog.csdn.net/cga6741011/article/details/50385022)
- [\[IOS\] Xcode创建子工程以及工程依赖](http://blog.csdn.net/u012703795/article/details/24978403)
- [iOS下OpenGL ES 3.0编程入门](http://www.th7.cn/Program/IOS/201508/521719.shtml)
- [OpenGL ES Programming Guide for iOS](https://developer.apple.com/library/prerelease/content/documentation/3DDrawing/Conceptual/OpenGLES_ProgrammingGuide/DrawingWithOpenGLES/DrawingWithOpenGLES.html#//apple_ref/doc/uid/TP40008793-CH503-SW5)
