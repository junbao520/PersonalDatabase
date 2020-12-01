## Jest 基础应用



### 前置知识

1. JavaScript（ES6）：对基本语法要比较熟悉，遇到的 JavaScript 知识和 ES6 知识。
2. Node.js ： 会使用包管理 npm。
3. git： git 的相关操作。

### Jest 优点

#### 主流的js测试框架

- Jasmine ： JavaScript 测试框架（BDD-集成测试开发框架），这个也算是比较早的测试框架。
- MOCHA: 它是一个功能丰富的 JavaScript 测试框架，运行在 Node.js 和浏览器中，使异步测试变得简单有趣。也是非常优秀的框架，但是我们公司没有用，所以我也什么发言权。
- Jest：目前最流行的前端测试框架，几乎国内所有的大型互联网公司都在使用。  
  其实这三个框架用起来都差不多，如果你能学会一个，自己再稍微学习一下，就可以迅速掌握其它两个。

#### 测试框架优点介绍

- 比较新：Jest是由facebook发布的，最近比较火热的一个测试框架。
- 基础很好：框架基础好就是性能好、功能多、简单易用。
- 速度快： 单独模块测试功能，比如说有两个模块 A 和 B，以前都测试过了，这时候你只改动 A 模块，才次测试，模块 B 不会再跑一次，而是直接测试 A 模块。
- API 简单 ：API 非常简单，数量也少。
- 隔离性好：Jest 里会有很多的测试文件等待我们使用，Jest 的执行环境都是隔离，这样就避免不同的测试文件执行的时候互相影响而造成出错。
- IDE 整合：Jest 直接可以和很多编辑器（VSCode）进行融合，让测试变的更加简单。
- 多项目并行：比如我们写了 Node.js 的后台项目，用 React 写了一个前台项目，Jest 是支持他们并行运行，让我们的效率更加提高了。
- 快出覆盖率：（测试代码覆盖率） 对于一个项目的测试都要出覆盖率的，Jest 就可以快速出这样的覆盖率统计结果，非常好用。

### 环境搭建（VSCode）

#### 安装 Jest 框架

```js
npm install jest@24.8.0 -D //-D 就保存到dev里边了，上线的时候我们不使用这个包，只有在开发的时候才进行测试。这样就安装完了Jest框架。
```

#### 入门案例

VSCode 的终端窗口中输入 npm run test，就可以进行测试了

```js
PASS  ./file1.test.js
PASS  ./file2.test.js

Test Suites: 2 passed, 2 total
Tests:       4 passed, 4 total
Snapshots:   0 total
Time:        2.581s
Ran all test suites.
```

### 基本测试及测试覆盖率

1. 单元测试和集成测试的区别

- 单元测试：英文是(unit testing) 单,是指对软件中的最小可测试单元进行检查和验证。单元测试就是对一个模块进行测试。

- 集成测试：也叫组装测试或者联合测试。在单元测试的基础上，将所有模块按照涉及要求组装成为子系统或系统，进行集成测试。

2. 初始化配置

```js
npx jest --init
```

之后会有一些选项，进行选择就可以了：

- Choose the test environment that will be used for testing ? 代码是运行在 Node 环境还是 Web 环境下？
- Do you want Jest to add coverage reports ? 是否生成测试覆盖率文件？
- Automatically clear mock calls and instrances between every test?是否需要在测试之后清楚模拟调用的一些东西？

在这三个选项选择之后，你会发现你的工程根目录下多了一个 jest.config.js 的文件。打开文件你可以看到里边有很多 Jest 的配置项。

code coverage,代码测试覆盖率，就是我们的测试代码，对功能性代码和业务逻辑代码作了百分多少的测试，这个百分比，就叫做代码测试覆盖率。

coverageDirectroy 的配置是用来打开代码覆盖率的，如果我们把代码写成下面的样子,就说明打开了代码覆盖率的这个选项。

```js
# 配置
coverageDirectory : "coverage"   //打开测试覆盖率选项
# 运行
npx jest --coverage

# 我们可以打开coverage-lcov-reporrt-index.html文件，这时候就可以看到一个网页形式的测试覆盖率报告。

# 快捷配置
 "scripts": {
    "test": "jest",
    "coverage":"jest --coverage"
  },
# node run coverage
```

### Jest 匹配器

1.  toBe()   ===  
     toBe()匹配器，是在工作中最常用的一种匹配器，简单的理解它就是相等。这个相当是等同于===的，也就是我们常说的严格相等。

    ```js
    test("测试严格相等", () => {
      const a = { number: "007" };
      expect(a).toBe({ number: "007" });
    });
    ```

    我们可以知道，这个不是完全相等的，引用地址不同，所以测试应该是 FAIL

2.  toEqual()  
    我想让上面的测试结果是正确的，使用 toEqual()匹配器。可以把它理解成只要内容相等，就可以通过测试，比如修改代码如下:

    ```js
    test("测试内容相等", () => {
      const a = { number: "007" };
      expect(a).toEqual({ number: "007" });
    });
    ```

    所以说当不严格匹配但要求值相等时时就可以使用 toEqual（）匹配器。

3.  toBeNul()  
     toBeNul()匹配器只匹配 null 值，需要注意的是不匹配 undefined 的值。代码修改成如下形式：

    ```js
    test("toBeNull测试", () => {
      const a = null;
      expect(a).toBeNull();
    });
    ```

    但是如果我们把 a 的值改为 undefined，测试用例就通过不了。

4.  toBeUndifined()  
     那我们要匹配 undefined 时，就可以使用 toBeUndifined()匹配器，比如写成如下代码。

    ```js
    test("toBeUndefined 测试", () => {
      const a = undefined;
      expect(a).toBeUndefined();
    });
    ```

    如果我们把 undefined 改为空字符串也是没有办法通过测试的。

5.  toBeDefined()匹配器的意思是只要定义过了，都可以匹配成功，例如下面的代码：

    ```js
    test("toBeDefined 测试", () => {
      const a = "jspang";
      expect(a).toBeDefined();
    });
    ```

    这里需要注意的是，我给一个 null 值也是可以通过测试的。

6.  stoBeTruthy  
    这个是 true 和 false 匹配器，就相当于判断真假的。比如说写下面这样一段代码:

    ```js
    test("toBeTruthy 测试", () => {
      const a = 0;
      expect(a).toBeTruthy();
    });
    ```

    这样测试就过不去了，因为这里的 0，如果判断真假时，就是 false，所以无法通过。同样道理 null 也是无法通过的。 但是我们给个 1 或者字符串，就可以通过测试了。

7.  toBeFalsy()  
    有真就有假，跟 toBeTruthy()对应的就是 toBeFalsy,这个匹配器只要是返回的 false 就可以通过测试。

    ```js
    test("toBeFalsy 测试", () => {
      const a = 0;
      expect(a).toBeFalsy();
    });
    ```

8.  toBeGreaterThan  
    这个是用来作数字比较的，大于什么数值，只要大于传入的数值，就可以通过测试。

    ```js
    test("toBeGreaterThan 匹配器", () => {
      const count = 10;
      expect(count).toBeGreaterThan(9);
    });
    ```

9.  toBeLessThan  
    toBeLessThan 跟 toBeGreaterThan 相对应的，就是少于一个数字时，就可以通过测试。代码如下:

    ```js
    test("toBeLessThan 匹配器", () => {
      const count = 10;
      expect(count).toBeLessThan(11);
    });
    ```

    比 11 小，所以测试用例顺利通过。

10. toBeGreaterThan  
    当测试结果数据大于等于期待数字时，可以通过测试。比如下面的代码是没办法通过测试的。

    ```js
    test("toBeGreaterThan 匹配器", () => {
      const count = 10;
      expect(count).toBeGreaterThan(10);
    });
    ```

    但是我们使用了 toBeGreaterThanOrEqual()就可以通过测试。

    ```js
    test("toBeGreaterThanOrEqual 匹配器", () => {
      const count = 10;
      expect(count).toBeGreaterThanOrEqual(10);
    });
    ```

11. toBeCloseTo  
    这个是可以自动消除 JavaScript 浮点精度错误的匹配器，举个例子，比如我们让 0.1 和 0.2 相加，这时候 js 得到的值应该是 0.30000000000004,所以如果用 toEqual()匹配器，测试用例会通过不了测试的。

    比如我们把测试用例写成这样，就不会通过:

    ```js
    test("toEqual 匹配器", () => {
      const one = 0.1;
      const two = 0.2;
      expect(one + two).toEqual(0.3);
    });
    ```

    这时候我们就需要使用 toBeCloseTo()匹配器，可以顺利通过测试,代码如下：

    ```js
    test("toBeCloseTo 匹配器", () => {
      const one = 0.1;
      const two = 0.2;
      expect(one + two).toBeCloseTo(0.3);
    });
    ```

    这样就可以顺利通过测试了，这就是它的作用。

12. toMatch()匹配器
    字符串包含匹配器，比如培训学校有三个老师：谢老师、刘老师和小红，这时候我们要看看字符串中有有谢老师就可以使用 toMatch()匹配器。

    ```js
    test("toMatch 匹配器", () => {
      const str = "谢老师、刘老师、小红";
      expect(str).toMatch("谢老师");
    });
    ```

    因为确实有“谢老师”,所以就通过测试了，当然你也可以写正则表达式。

    ```js
    test("toMatch 匹配器", () => {
      const str = "谢老师、刘老师、小红";
      expect(str).toMatch(/谢老师/);
    });
    ```

    我们可以开启 node run test 就可以看到测试结果也是正确的。

13. toContain()匹配器

    刚才我们使用的只是一个字符串包换关系的匹配器，但是在工作中使用的多是数组，所以这里我们使用数组的匹配器 toContain()。比如还是上面象牙山洗脚城的案例，我们就可以写成这样。

    ```js
    test("toContain 匹配器", () => {
      const arr = ["谢老师", "刘老师", "小红"];
      expect(arr).toContain("谢老师");
    });
    ```

    当然他也可以完美的兼容 set 的测试，比如把下面代码改为下面的方式。

    ```js
    test("toContain 匹配器", () => {
      const arr = ["谢老师", "刘老师", "小红"];
      const data = new Set(arr);
      expect(data).toContain("谢老师");
    });
    ```

14. toThrow()匹配器

    

    匹配器参考
    Jest 当中有很多匹配器，这里给出官方文档： https://jestjs.io/docs/en/expect

### 异步代码测试方法

1.  回调函数式

    fetchData.js

    ```js
    export const fetchData = (fn) => {
      axios.get("http://a.jspang.com/jestTest.json").then((response) => {
        fn(response.data);
      });
    };
    ```

    编写测试方法
    有了这个文件，接下来就可以写测试文件 fetchData.test.js.在项目根目录下，新建一个 fetchData.test.js 文件，然后编写下面的代码。

    ```js
    const { fetchData } = require("./fetchData.js");

    test("fetchData 测试", () => {
      fetchData((data) => {
        expect(data).toEqual({
          success: true,
        });
      });
    });
    ```

    备注：注意这样写是有问题的，因为方法还没有等到回调，我们的结果已经完成了，所以这时候你对于没测试完，只是方法可用，就返回了测试结果，这种结果是不保证正确的。

    比如现在我们把请求的地址后边加一个 1,这时候才测试，依然是正确的。

    ```js
    axios.get("http://a.jspang.com/jestTest1.json").then((response) => {
      fn(response.data);
    });
    ```

    所以我们必须加入一个 done 方法，保证我们的回调已经完成了，这时候我们表示测试完成。

    ```js
    const { fetchData } = require("./fetchData.js");

    test("fetchData 测试", (done) => {
      fetchData((data) => {
        expect(data).toEqual({
          success: true,
        });
        done();
      });
    });
    ```

    这时候我们的测试代码才能保证测试准确无误的完成，所以你在工作中处理异步函数的时候，一定要注意这种异步函数的形式如何来进行测试。

2.  直接返回 Promise

    上面是异步的一种方式，还有一种方式直接返回一个 promise 值，这样的方法在工作中也式经常使用的。
    测试代码：

    ```js
    export const fetchTwoData = () => {
      return axios.get("http://a.xxxxxx.com/jestTest.json");
    };
    ```

    从代码中可以看出，我们直接只用了 Return 返回了异步请求的 promise 值，这样的方法在实际工作中也经常使用，这里也是有坑的。

    编写测试代码
    打开 fetchData.test.js 文件，然后新写一个测试用例，在写之前记得先把 fetchTwoData 方法引过来。

    ```js
    const { fetchData, fetchTwoData } = require("./fetchData.js");
    // 引入之后，编写测试用例，代码如下:

    test("FetchTwoData 测试", () => {
      return fetchTwoData().then((response) => {
        expect(response.data).toEqual({
          success: true,
        });
      });
    });
    ```

    这部分代码需要注意的是要使用 return 才能测试成功，希望大家不要踩坑。

3.  接口不存在
    在工作中有时候会测试异步接口不存在的需求，比如有些后台需求不允许前台访问时，这时候就会返回 404（不存在）。
    编写异步代码
    继续打开 fetchData.test.js 文件，然后编写测试代码如下，注意这个地址是不存在的，也就是返回 404。

    ```js
    export const fetchThreeData = () => {
      return axios.get("http://a.xxxxxx.com/jestTest_error.json");
    };
    ```

    编写测试代码
    测试 404 直接用 catch 就可以了，很简单，然后代码写成了这样。

    ```js
    test("FetchThreeData 测试", () => {
      return fetchThreeData().catch((e) => {
        //console.log(e.toString())
        expect(e.toString().indexOf("404") > -1).toBe(true);
      });
    });
    ```

    但这样是错误的，比如现在我们把异步请求代码改正确后，我们再走一下测试，还是可以通过测试的。 现把网址改成正确的:

    http://a.xxxxxx.com/jestTest.json

    那这是为什么呢？因为测试用例使用了 catch 方法，也就是说只有出现异常的时候才会走这个方法，而在没有出现异常，就不会走这个测试方法，Jest 就默认这个用例通过了测试。

    这个也算是一个坑，想改这个坑也非常简单，只要使用 expect.assertions(1)就可以了，这个代码的意是“断言，必须需要执行一次 expect 方法才可以通过测试”。

    修改过后的代码就变成了这个样子

    ```js
    test("FetchThreeData 测试", () => {
      expect.assertions(1); // 断言，必须执行一次 expect
      return fetchThreeData().catch((e) => {
        expect(e.toString().indexOf("404") > -1).toBe(true);
      });
    });
    ```

    这时候测试用例就无法正常通过测试了，因为此时我们的地址是存在并正确返回结果的。我们需要改成错误的地址，才能通过测试。

        http://a.xxxxxx.com/jestTest_error.json

    我们会了正常的，也会了不正常的测试方法，组合起来用就会让测试变的强大的多，比如测试正常的时候是如何的，碰到不正常，应该是如何的。这也基本组成了我们异步测试的基本结构，就是不仅要测试正常情况，正常流程的代码，也要测试异常情况和突发情况下的代码健壮性。

4.  async...await 编写测试代码
    这时候我们的代码使用 async....await...的形式，这里我们还使用了 resolves 用于把现有对象转换成 Promise 对象，然后使用 Jest 中的 toMatchObject 进行匹配对象中的属性。

    ```js
    test("FetchFourData 测试", async () => {
      //resolves 把现有对象转换成 Promise 对象，
      //toMatchObject 匹配对象中的属性
      await expect(fetchFourData()).resolves.toMatchObject({
        data: {
          success: true,
        },
      });
    });
    ```

    写完上面的代码就可以出正确的结果了，但是这种方法还是有点抽象的，需要用 resolves 转换一下。

    也可以把上面的测试方法写成这样：

    ```js
    test("FetchFourData 测试", async () => {
      const response = await fetchFourData();
      expect(response.data).toEqual({
        success: true,
      });
    });
    ```

    这就是用 async...await...来进行异步代码测试。

### Jest 钩子函数

- beforeAll()钩子函数
  beforeAll()钩子函数的意思是在所有测试用例之前进行执行。

  ```js
  beforeAll(() => {
    console.log("beforeAll:上学了");
  });
  ```

- afterAll()钩子函数
  afterAll()钩子函数是在完成所有测试用例之后才执行的函数。

  ```js
  afterAll(() => {
    console.log("afterAll：放学了");
  });
  ```

- beforeEach()钩子函数
  beforeEach()钩子函数，是在每个测试用例前都会执行一次的钩子函数，比如我们写如下代码。

  ```js
  beforeEach(() => {
    console.log("上课铃声响了......");
  });
  ```

  保存后可以看到，每个测试用例执行之前都会先执行一下这个函数。

- afterEach()钩子函数
  afterEach()钩子函数，是在每次测试用例完成测试之后执行一次的钩子函数，比如下面的代码。

  ```js
  afterEach(() => {
    console.log("下课铃声响了......");
  });
  ```

  在工作中最常用的四个钩子函数就是这四个函数了，这里举了一个简单的例子:

  ```js
  beforeAll(() => {
    console.log("去学校上学啦......");
  });

  beforeEach(() => {
    console.log("上课了......");
  });

  test("测试 上英语课 方法", () => {
    expect(shangke.kecheng).toEqual("上英语课");
  });

  test("测试 上数学课 方法", () => {
    expect(shangke.kecheng).toEqual("上数学课");
  });

  afterEach(() => {
    console.log("轻松上完一节课！！！");
  });

  afterAll(() => {
    console.log("终于放学了......");
  });
  ```

### 测试分组方法编写

随着课程的不断增多，我们是时候出个分老师服务了，毕竟每个学生的课有限，不可能全部都参与。所以就需要进行分组。

那最原始的方法是，我们新建两个测试文件，把谢老师的课放到一个测试文件里，把刘老师的测试文件放到一个文件里去，这就形成了分组。

但这样分组显然是不够优雅的，毕竟我们需要测试的代码在一个文件里，我们的测试文件却分成了两个文件。

其实 Jest 为我们提供了一个分组的语法 describe(),这个方法接受两个参数，现在我们把谢老师和刘老师的测试用例用 describe()方法进行分开。代码如下:

```js
import ShangKe from "./shangke.js";
const shangke = new ShangKe();
beforeAll(() => {
  console.log("去学校上学啦......");
});

beforeEach(() => {
  console.log("上课了......");
});

describe("谢老师相关课程", () => {
  test("测试 谢老师 英语I 方法", () => {
    expect(shangke.kecheng).toEqual("谢老师 英语I");
  });

  test("测试 谢老师 英语II 方法", () => {
     expect(shangke.kecheng).toEqual("谢老师 英语I");
  });
});

describe("刘老师相关课程", () => {
  test("测试 刘老师 数学I 方法", () => {
    expect(shangke.kecheng).toEqual("刘老师 数学I");
  });
  test("测试 刘老师 数学II  方法", () => {
    expect(shangke.kecheng)..toEqual("刘老师 数学II");
  });
});

afterEach(() => {
  console.log("轻松上完一节课！！！");
});

afterAll(() => {
  console.log("终于放学了......");
});
```

这样分组的好处实际就就是要让测试用例看起来更有层次感。

### 钩子函数的作用域

其实我们学习了 describe 分组，关系到钩子作用域。Jest 中钩子函数的作用域有下面三个特色。

- 钩子函数在父级分组可作用域子集，类似继承
- 钩子函数同级分组作用域互不干扰，各起作用
- 先执行外部的钩子函数，再执行内部的钩子函数

钩子函数在父级分组可作用域子集
为了更好的说明钩子函数的作用域，现在我们把程序的最外层加入一个 describe，其实不加这个，系统默认也是有这个的，只是不那么直观。

加入 describe,代码如下：

```js
describe("最外层分组", () => {
  beforeAll(() => {
    console.log("beforeAll");
  });

  beforeEach(() => {
    console.log("beforeEach......");
  });

  describe("谢老师相关课程", () => {
    test("测试 谢老师 英语I 方法", () => {
        expect(shangke.kecheng).toEqual("谢老师 英语I");
      });

      test("测试 谢老师 英语II 方法", () => {
         expect(shangke.kecheng).toEqual("谢老师 英语I");
      });
    });

    describe("刘老师相关课程", () => {
      test("测试 刘老师 数学I 方法", () => {
        expect(shangke.kecheng).toEqual("刘老师 数学I");
      });
      test("测试 刘老师 数学II  方法", () => {
        expect(shangke.kecheng).toEqual("刘老师 数学II");
      });
    });

  afterEach(() => {
    console.log("轻松上完一节课！！！");
  });

  afterAll(() => {
    console.log("终于放学了......");
  });
});
```

写完后你在控制台运行 node run test，可以看到 console.log 的顺序和结果并没有改变。并且每一个 beforeEach 和 afterEach 也都在每一个测试用例的前后执行了。这就是我们说的第一条钩子函数在父级分组可作用域子集，类似继承

**钩子函数同级分组作用域互不干扰**
现在“谢老师”和“刘老师”都希望在课后布置一些作业。这时候就可以在两个同级的 describe 中分别加入不同的 afterEach。

```js
afterEach(() => {
  console.log("------谢老师的作业");
});

afterEach(() => {
  console.log("------刘老师的作业");
});
```

这个案例也说明了钩子函数在同级的 describe 分组里是互不干扰的。

**先执行外部的钩子函数**

test 测试用例这里加入一个 only，加入后，其它的用例都会 skipped 掉，只执行这一个。

```js
test.only("测试 XXX 方法", () => {
  expect(shangke.kecheng).toEqual("XXX");
});
```

这个例子正好说明了，外部的钩子函数先执行，下级的分组后执行，也就是执行顺序是“由外到内”的.only 的使用在工作中也是经常使用的，因为有时候测试用例很多，不好调试，就可以使用 only 的形式单独调试。



### 参考：

https://jestjs.io/docs/en/expect

