###iOS Project Toolchain

CocoaPods安装：
- [CocoaPods安装和使用教程](http://code4app.com/article/cocoapods-install-usage)
- [iOS可持续化集成](http://blog.csdn.net/colorapp/article/details/47007329)
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
