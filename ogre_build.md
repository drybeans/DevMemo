###Ogre-1-9-0各平台上编译

> 如果不想编译Samples，可以在顶级目录下的CMakeLists.txt寻找add_subdirectory(Samples),
  将其改为add_subdirectory(Samples EXCLUDE_FROM_ALL)

> Cmake为v2.8.12或者v3.4.3均可

####Windows下编译Visual Studio版本
- 拷贝[OgreDependencies](https://github.com/drybeans/OgreDependencies)目录下的Dependencies目录到Ogre源代码目录下（和OgreMain同级目录）
- 在Ogre目录下新创建Builds/Win32目录
- 直接打开cmake-gui程序
- “Where is the source code”定位到Ogre源代码目录，也就是顶级CMakeLists.txt存在的目录
- “Where to build the binaries”定位到上面创建的Builds/Win32目录
- 点击左中角Configure按钮，再次点击Configure
- 点击Generate按钮
- 出现提示框，选择合适编译器即可，双击打开Builds/Win32目录下的OGRE.sln即可

####Mac(OSX 10.11.4 x86_64版本)下编译iOS版本
- 拷贝[OgreDependencies](https://github.com/drybeans/OgreDependencies)目录下的iOSDependencies目录(打开里面的dmg文件，拷贝include以及lib出来)到Ogre源代码目录下（和OgreMain同级目录）
- 安装命令行cmake（通过[Homebrew](http://www.jianshu.com/p/f9b2c74cb519)或其他方式均可）
- 在Ogre目录下mkdir -p Buils/iOS && cd Builds/iOS
- 执行：cmake -D OGRE_BUILD_PLATFORM_APPLE_IOS=1 -G Xcode ../..
- 在Buils/iOS目录下双击OGRE.xcodeproj即可

> 编译的过程中会提示：iOSDendencies中有几个依赖库不支持armv7，但是是支持arm64的。
  关于这个，大家可以直接编译arm64的即可（iPhone5s之后支持arm64），如果实在需要编译armv7的，可以拷贝[OgreDependencies](https://github.com/drybeans/OgreDependencies)源码，到自己机器上编译。
  另外可以用[lipo](http://ss64.com/osx/lipo.html)这个命令来查看库的状态或者对库进行瘦身/合成操作
  
####Mac(OSX 10.11.4 x86_64版本)下编译Android版本，android-ndk-r9d
- 拷贝[OgreDependencies](https://github.com/drybeans/OgreDependencies)目录下的AndroidDependencies目录到Ogre源代码目录下（和OgreMain同级目录）
- 安装命令行cmake（通过[Homebrew](http://www.jianshu.com/p/f9b2c74cb519)或其他方式均可）
- 在Ogre目录下mkdir -p Builds/Android && cd Builds/Android
- 修改CMake/toolchain/android.toolchain.cmake文件：
  - set( ANDROID_SUPPORTED_NDK_VERSIONS ${ANDROID_EXTRA_NDK_VERSIONS} -r8e -r8d -r8b -r7c -r7b -r7 -r6b -r6 -r5c -r5b -r5 "" )
    改为：set( ANDROID_SUPPORTED_NDK_VERSIONS ${ANDROID_EXTRA_NDK_VERSIONS} -9d -r8e -r8d -r8b -r7c -r7b -r7 -r6b -r6 -r5c -r5b -r5 "" )
  - 由于本地装的是x86_64的，则set( ANDROID_NDK_HOST_SYSTEM_NAME "darwin-x86" )
    改为：set( ANDROID_NDK_HOST_SYSTEM_NAME "darwin-x86_64" )
- 修改CMake/toolchain/AndroidJNI.cmake
  - 由于cmake运行到该脚本出，APPLE这个变量会失效，可将if(APPLE OR WIN32)改为：if(CMAKE_HOST_APPLE OR WIN32)
- 最后执行：cmake -DCMAKE_TOOLCHAIN_FILE="../../CMake/toolchain/android.toolchain.cmake" -DOGRE_DEPENDENCIES_DIR="../../AndroidDependencies" -DANDROID_ABI=armeabi-v7a  -DANDROID_NATIVE_API_LEVEL=17 -DANDROID_TOOLCHAIN_NAME=arm-linux-androideabi-4.8 ../..
  - 其中“-DANDROID_NATIVE_API_LEVEL=17“，这个17需要保证mac上设置了android sdk路径以及有sdk这个版本(Android-4.2)
- 执行：~/Documents/AndroidDev/android-ndk-r9d/prebuilt/darwin-x86_64/bin/make

> 如有需要，需设置(export) ANDROID_NDK ANDROID_SDK 

####可用链接
- [Ogre源码编译教程](http://www.cnblogs.com/woud/p/4749340.html)
