# jctpapi-linux
### 使用[SWIG](http://www.swig.org/)生成用于Java调用上期技术CTP-API的JNI（C++）源码

#### 简介

本仓库提供 [redtorch](https://github.com/sun0x00/redtorch) 项目的rt-gateway-ctp模块的具体代码生成方法和跨平台运行方案细节。

#### 使用方法
+ 准备GCC编译环境
+ 安装JDK，并设置JAVA_HOME到环境变量中（编译需要访问使用jni.h和jni_md.h）
+ 编译获取libiconv.a静态链接库
   - 使用仓库中提供的压缩包或从[libiconv官网](https://www.gnu.org/software/libiconv/)下载压缩包
   - 在解压后的目录中执行configure命令
      ```
      ./configure --prefix=<目标目录> --enable-static=yes CFLAGS=-fPIC
      ```
      例如
      ```
      ./configure --prefix=/home/sun0x00/libiconv-1.15-target --enable-static=yes CFLAGS=-fPIC
      ```
      目标目录请根据实际情况修改
    - 执行编译命令
      ```
      make && make install
      ```
    - 访问目标目录下的lib文件夹，获取libiconv.a文件，并将此文件复制到各版本CTP的工作目录中
 + 在各版本CTP的工作目录中，分别执行make命令，即可获得封装后的链接库
 + 在各版本CTP的工作目录中，分别执行make clen命令，即可清除封装后的链接库

#### 提示
+ 本仓库中提供的JNI(C++)源码来自仓库 [swig-java-ctp](https://github.com/sun0x00/swig-java-ctp)
+ 本仓库中提供的链接库so文件来自[上期技术官网](www.sfit.com.cn)提供的各对应版本的SDK压缩包
+ Windows环境下的编译方法请访问仓库 [jctpapi-msvc](https://github.com/sun0x00/jctpapi-msvc)
+ 本仓库中提供的JNI(C++)源码已经解决CTP结算单乱码问题，具体实现细节请访问仓库 [swig-java-ctp](https://github.com/sun0x00/swig-java-ctp)




