



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





```c++
//基于NAPI Demo
//#include <napi.h> windows linux 都可执行 对Node版本没有强一直要求
Napi::Value intersectionPositioning(const Napi::CallbackInfo &info)

  {

   Napi::Env env = info.Env();

 if (info.Length() <= 0 || !info[0].IsObject())

 {

    Napi::TypeError::New(env, "Object expected").ThrowAsJavaScriptException();

  }

  Napi::Object obj = info[0].ToObject();



   int pointLen = (int)obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "pointLen"))).As<Napi::Number>().DoubleValue();

  int azimuthNLength = (int)obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "azimuthNLength"))).As<Napi::Number>().DoubleValue();

  double mindistance = obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "mindistance"))).As<Napi::Number>().DoubleValue();



 Napi::Array input_array = obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "angleindex"))).As<Napi::Array>();

 int length = input_array.Length();



int *angleindex = new int[length];

 for (int i = 0; i < length; i++)

  {

    angleindex[i] = static_cast<Napi::Value>(input_array[i]).As<Napi::Number>().DoubleValue();

   }



  input_array = obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "azimuthN"))).As<Napi::Array>();

   length = input_array.Length();

   float *azimuthN = new float[length];

   for (int i = 0; i < length; i++)

   {

     azimuthN[i] = (float)static_cast<Napi::Value>(input_array[i]).As<Napi::Number>().DoubleValue();

   }



   input_array = obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "lat"))).As<Napi::Array>();

    length = input_array.Length();

   double *lat = new double[length];

   for (int i = 0; i < length; i++)

    {

     lat[i] = static_cast<Napi::Value>(input_array[i]).As<Napi::Number>().DoubleValue();

  }



  input_array = obj.Get(static_cast<napi_value>(Napi::String::New(info.Env(), "lon"))).As<Napi::Array>();

   length = input_array.Length();

   double *lon = new double[length];

    for (int i = 0; i < length; i++)

    {

     lon[i] = static_cast<Napi::Value>(input_array[i]).As<Napi::Number>().DoubleValue();

    }

   double *result = new double[100];

   int resultLen = 0;

   SingleStationLocate(pointLen, lon, lat, angleindex, azimuthNLength, azimuthN, result, mindistance, resultLen);


   Napi::Object objOut = Napi::Object::New(env);

    Napi::Number num = Napi::Number::New(env, resultLen);

   Napi::Array resultArray = Napi::Array::New(env, resultLen);



  for (int i = 0; i < resultLen; i++)

    {

    resultArray[i] = result[i];

  }



   objOut.Set(Napi::String::New(env, "resultLen"), resultLen);

   objOut.Set(Napi::String::New(env, "result"), resultArray);

   //obj.Set(Napi::String::New(env, "msg"), info[0].ToString());

    return objOut;

  }
```



```c++
//基于Node Api 的Demo windows linux 都可以执行 但是要求版一致 //Welcome to Node.js v12.13.1.
#include <node.h>

namespace datas
{
    using namespace v8;
    using namespace std;

    using v8::Context;
    using v8::Exception;
    using v8::Function;
    using v8::FunctionCallbackInfo;
    using v8::FunctionTemplate;
    using v8::Isolate;
    using v8::Local;
    using v8::Number;
    using v8::Object;
    using v8::String;
    using v8::Value;

    static void Datas(const FunctionCallbackInfo<Value> &args)
    {
        Isolate *isolate = args.GetIsolate();
        Local<Array> input_array = Local<Array>::Cast(args[0]);
        int length = input_array->Length();
        double* angleindex = new double[length];
        for (int i = 0; i < length; i++)
        {
            angleindex[i] = input_array->Get(i).As<Number>()->Value();
        }
        input_array = Local<Array>::Cast(args[1]);
        length = input_array->Length();
        double* azimuthN = new double[length];
        for (int i = 0; i < length; i++)
        {
            azimuthN[i] = input_array->Get(i).As<Number>()->Value();
        }
        double mindistance = args[2].As<Number>()->Value();
        int pointLen = args[3].As<Number>()->Value();

        // 声明一个V8的Object类型的变量
        Local<Object> object = Object::New(isolate);
        // 声明一个V8的Array类型的变量
        Local<Array> angleindexArray = Array::New(isolate);
        Local<Array> azimuthNArray = Array::New(isolate);
        Local<Number> mindistanceNumber = Number::New(isolate, mindistance);
        Local<Number> pointLenNumber = Number::New(isolate,pointLen);
        // 给array赋值
        //sizeof(array) / sizeof(array[0])
        length=sizeof(angleindex);
        //printf("angleindex %d",length);
        for (int i = 0; i <length; ++i)
        {
            angleindexArray->Set(i, Number::New(isolate, angleindex[i]));
        }
        length=sizeof(azimuthN);
        printf("azimuthN %d",length);
        for (int i = 0; i <length; ++i)
        {
            azimuthNArray->Set(i, Number::New(isolate, azimuthN[i]));
        }
        object->Set(String::NewFromUtf8(isolate, "angleindex"), angleindexArray);
        object->Set(String::NewFromUtf8(isolate, "azimuthN"),azimuthNArray);
        object->Set(String::NewFromUtf8(isolate, "mindistance"),  mindistanceNumber);
        object->Set(String::NewFromUtf8(isolate, "pointLen"), pointLenNumber);
        args.GetReturnValue().Set(object);
    }

    static void init(Local<Object> exports, Local<Object> module)
    {
        // NODE_SET_METHOD(module, "exports", Datas);

        NODE_SET_METHOD(exports, "data", Datas);
    }

    //     void init1(Local<Object> exports) {
    //   NODE_SET_METHOD(exports, "hello", Method);
    // }

    // NODE_MODULE(hello, init1)

    NODE_MODULE(NODE_GYP_MODULE_NAME, init)
} // namespace datas
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

