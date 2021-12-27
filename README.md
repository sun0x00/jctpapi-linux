# jctpapi-linux
### 在Linux环境下使用GCC编译Java调用上期技术CTP-API的JNI（C++）源码

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
    - 访问目标目录下的lib文件夹，获取libiconv.a文件，并将此文件复制到各版本Java-CTP的工作目录中
 + 在各版本Java-CTP的工作目录中，分别执行make命令，即可获得封装后的链接库
 + 在各版本Java-CTP的工作目录中，分别执行make clen命令，即可清除封装后的链接库

#### 提示
+ 本仓库中提供的JNI(C++)源码来自仓库 [swig-java-ctp](https://github.com/sun0x00/swig-java-ctp)
+ 本仓库中提供的链接库so文件来自[上期技术官网](www.sfit.com.cn)提供的各对应版本的SDK压缩包
+ 如果尝试自建空白项目，请参考现存版本文件夹的内容准备文件，注意，需要重命名上上期技术提供的两个.so文件,分别在文件名之前加lib
+ Windows环境下的编译方法请访问仓库 [jctpapi-msvc](https://github.com/sun0x00/jctpapi-msvc)
+ 本仓库中提供的JNI(C++)源码已经解决CTP结算单乱码问题，具体实现细节请访问仓库 [swig-java-ctp](https://github.com/sun0x00/swig-java-ctp)
+ 关于编译后lib文件的使用，在makefile文件中存在如下配置
   ```
   LD_RUN_PATH=-Wl,-rpath,/tmp/xyz/redtorch/api/jctp/lib/jctpv6v6v1p1cpx64api/
   ```
   在实际使用过程中，编译后的链接库so文件可不安装到系统lib目录，复制到/tmp/xyz/redtorch/api/jctp/lib/jctpv6v6v1p1cpx64api/，可在Java代码中通过绝对路径加载。
+ Linux环境下编译的Java-CTP链接库在使用时无需加载libiconv.so
+ 编译后的Java-CTP链接库使用方法请参阅[redtorch](https://github.com/sun0x00/redtorch) 项目的rt-gateway-ctp模块



