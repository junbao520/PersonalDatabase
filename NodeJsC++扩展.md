



# **Node js c++ 扩展 **

1.首先安装Python 环境(推荐2.7，其他版本为测试，据说可以) 不安装 VS 也可以，但是需要VS的编译器

linux 下输入 python

Python 2.7.16 (default, Oct 10 2019, 22:02:15) 

理论上这些都支持，推荐是用2.7，其他版本可能要把Python加入环境变量。

 v2.7, v3.5, v3.6, v3.7, or v3.8.



```javascript
# 项目根目录 binding.gyp 文件
{

 "targets": [

  {

   "target_name": "algorithm",

   "cflags!": [ "-fno-exceptions" ],

   "cflags_cc!": [ "-fno-exceptions" ],

   "sources": [ "algorithm\IntersectionPositioning.cc" ],

   "include_dirs": [

    "<!@(node -p \"require('node-addon-api').include\")"

   ],

   'defines': [ 'NAPI_DISABLE_CPP_EXCEPTIONS' ],

  }

 ]

}
```

```javascript
# 使用方法

require('../algorithm/intersectionPositioning-windows.node')

algorithm.intersectionPositioning(jsonData);
```



```javascript
安装 node-gyp

#npm install -g node-gyp  或者  cnpm install -g node-gyp

node-gyp -v 输出 v 7.1.1 或者其他版本表示成功

#安装gcc

cnpm install gcc

gcc -v 检查gcc是否正确安装

#安装 g++

gcc是GCC中的GUN C Compiler（C 编译器）

g++是GCC中的GUN C++ Compiler（C++编译器）

#linux make 指令安装

#Debian、Ubuntu

apt-get update
apt-get install make

#Centos、Redhat下执行：

yum update
yum install make

#编译

Windows 上面执行 npm i 

linux   上面执行 node-gyp rebuild


```



# **Node ffi ** 

node-ffi 底层也是基于Nodejs C++ 扩展 N-API 实现的。

`node-ffi`通过`Buffer`类，在C代码和JS代码之间实现了内存共享，类型转换则是通过[ref](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2FTooTallNate%2Fref)、[ref-array](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2FTooTallNate%2Fref-array)、[ref-struct](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2FTooTallNate%2Fref-struct)实现。由于`node-ffi`/`ref`包含C原生代码，所以安装需要配置Node原生插件编译环境。

https://github.com/nodejs/node-gyp#installation

- Python v2.7, v3.5, v3.6, v3.7, or v3.8
- `make`
- A proper C/C++ compiler toolchain, like [GCC](https://gcc.gnu.org/)



问题 目前 npm i node-ffi 在windows 上尚未成功

npm i ffi-napi 可以安装成功 但是执行失败

