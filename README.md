# cmakelearn

```sh
$ cmake .	#get Makefile
$ make		#get executable file
$ sudo make install
$ make test
$ cpack -C CPackConfig.cmake
$ cpack -C CPackSourceConfig.cmake    #生成源码安装包
```

## 目录
- [demo1 单个源文件](demo1)
- [demo2 多个源文件](demo2)
- [demo3 自定义编译选项](demo3)
- [demo4 安装和测试](demo4)

需要删除才能重新生成config.h
```sh
$ sudo make install
[sudo] password for txcom-ubuntu64: 
[ 50%] Built target MathFunctions
[100%] Built target demo
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/demo
-- Installing: /usr/local/include/config.h
-- Installing: /usr/local/bin/libMathFunctions.a
-- Installing: /usr/local/include/MathFunctions.h
```

```sh
$ make test
Running tests...
Test project /home/txcom-ubuntu64/cmakelearn/demo5
    Start 1: test_run
1/5 Test #1: test_run .........................   Passed    0.00 sec
    Start 2: test_usage
2/5 Test #2: test_usage .......................   Passed    0.00 sec
    Start 3: test_5_2
3/5 Test #3: test_5_2 .........................   Passed    0.00 sec
    Start 4: test_10_5
4/5 Test #4: test_10_5 ........................   Passed    0.00 sec
    Start 5: test_2_10
5/5 Test #5: test_2_10 ........................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 5

Total Test time (real) =   0.01 sec
```

- [demo5 支持 gdb](demo5)
- [demo6 添加环境检查](demo6)
- [demo7 添加版本号](demo7)
- [demo8 生成安装包](demo8)
```sh
$ ./demo8-..1-Linux.sh 
demo8 Installer Version: ..1, Copyright (c) Humanity
This is a self-extracting archive.
The archive will be extracted to: /home/txcom-ubuntu64/cmakelearn/demo8

If you want to stop extracting, please press <ctrl-C>.
LICENSE
=======

This is an installer created using CPack (http://www.cmake.org). No license provided.



Do you accept the license? [yN]: 
y
By default the demo8 will be installed in:
  "/home/txcom-ubuntu64/cmakelearn/demo8/demo8-..1-Linux"
Do you want to include the subdirectory demo8-..1-Linux?
Saying no will install in: "/home/txcom-ubuntu64/cmakelearn/demo8" [Yn]: 
y

Using target directory: /home/txcom-ubuntu64/cmakelearn/demo8/demo8-..1-Linux
Extracting, please wait...

Unpacking finished successfully

$ cd demo8-..1-Linux/bin
$ ./demo 2 20
Now we use our own Math library. 
2 ^ 20 is 1.04858e+06
```

## content2
- 一， 初识 cmake
- 二， 安装 cmake
- [三， 初试 cmake – cmake 的 helloworld](t1)
```sh
$ cmake .
$ make

$ mkdir build
$ cd build
$ cmake ..
$ make
```
- [四 ， 更好一点的 Hello World](t2)
```sh
$ mkdir build && cd build
$ cmake ..
$ make
$ ./bin/hello

$ mkdir build && cd build
$ cmake -DCMAKE_INSTALL_PREFIX=/tmp/t2/usr ..
$ make
$ sudo make install
[100%] Built target hello
Install the project...
-- Install configuration: ""
-- Installing: /tmp/t2/usr/share/doc/cmake/t2/COPYRIGHT
-- Installing: /tmp/t2/usr/share/doc/cmake/t2/README
-- Installing: /tmp/t2/usr/bin/runhello.sh
-- Installing: /tmp/t2/usr/share/doc/cmake/t2
-- Installing: /tmp/t2/usr/share/doc/cmake/t2/hello.txt

```
- [五， 静态库与动态库构建](t3)

when i add  
`ADD_LIBRARY(hello SHARED ${LIBHELLO_SRC})
ADD_LIBRARY(hello_static STATIC ${LIBHELLO_SRC})`  
I get libhello.a

when i add  
`ADD_LIBRARY(hello SHARED ${LIBHELLO_SRC})
ADD_LIBRARY(hello_static STATIC ${LIBHELLO_SRC})
SET_TARGET_PROPERTIES(hello_static PROPERTIES OUTPUT_NAME "hello")`  
I get libhello.a and libhello.so

when i add  
`SET(LIBHELLO_SRC hello.c)
ADD_LIBRARY(hello SHARED ${LIBHELLO_SRC})
ADD_LIBRARY(hello_static STATIC ${LIBHELLO_SRC})
SET_TARGET_PROPERTIES(hello_static PROPERTIES OUTPUT_NAME "hello")
SET_TARGET_PROPERTIES(hello PROPERTIES CLEAN_DIRECT_OUTPUT 1)
SET_TARGET_PROPERTIES(hello_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)`  
I get the same result as 2
- [六， 如何使用外部共享库和头文件](t4)
```sh
#link to libhello.so
$ ldd src/main 
	linux-vdso.so.1 =>  (0x00007fff2ff99000)
	libhello.so.1 => /usr/local/lib/libhello.so.1 (0x00007f0e251a8000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0e24ddf000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f0e253aa000)
    
#link to libhello.a
$ ldd src/main 
	linux-vdso.so.1 =>  (0x00007ffd02519000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f44967e1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f4496baa000)
```
- 七， cmake 常用变量和常用环境变量
- 八， cmake 常用指令
- 九， 复杂的例子：模块的使用和自定义模块([t5](t5)、[t6](t6))
---------
[CMake 入门实战](https://www.hahack.com/codes/cmake/)  
[CMake实践]()
