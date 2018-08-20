###1、在 Android 中如何调用 C 语言  
当我们的 Java 需要调用 C 语言的时候可以通过 JNI 的方式，Java Native Interface。Android 提供了对 JNI 的支  
持，因此我们在Android中可以使用 JNI调用C 语言。在Android开发目录的 libs 目录下添加 xxx.so 文件，不过 xxx.so  
文件需要放在对应的 CPU 架构名目录下，比如 armeabi，x86 等。  
在 Java 代码需要通过 System.loadLibrary(libName); 加载 so 文件。同时 C 语言中的方法在 java 中必须  
以 native 关键字来声明。普通 Java 方法调用这个 native 方法接口，虚拟机内部自动调用 so 文件中对应的方法。  
### 2、请介绍一下 NDK  
#####  1.NDK 是一系列工具的集合  
NDK 提供了一系列的工具，帮助开发者快速开发 C（或 C++）的动态库，并能自动将 so 和 java 应用一起打包  
成 apk。NDK 集成了交叉编译器，并提供了相应的 mk 文件隔离 CPU、平台、ABI 等差异，开发人员只需要简单修  
改 mk 文件（指出“哪些文件需要编译”、“编译特性要求”等），就可以创建出 so。  
##### 2.NDK 提供了一份稳定、功能有限的 API 头文件声明  
Google 明确声明该 API 是稳定的，在后续所有版本中都稳定支持当前发布的 API。从该版本的 NDK 中看出，   
这些 API 支持的功能非常有限，包含有：C 标准库（libc）、标准数学库（libm）、压缩库（libz）、Log 库（liblog）。  
