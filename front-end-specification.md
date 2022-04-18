# 前端开发需要注意事项

## 命名规范

#### 基本原则：结构、样式、行为分离

- 样式都放到 CSS 样式表里，行为都放到 JS 脚本里

##### 项目命名

- 全部采用小写方式， 以中划线分隔。 mall-management-system

#### 文件/资源命名

- 使用连字符（-）来分隔文件名 `order-detail-view.js`
- 确保不用大写字母开头，不要驼峰命名。

##### 目录命名

- 全部采用小写方式， 以中划线分隔，有复数结构时，要采用复数命名法， 缩写不用复数

  - scripts / styles / components / images / utils / layouts / demo-styles / demo-scripts / img / doc

- 使用 kebab-case 命名

  - head-search / page-loading / authorized / notice-icon

- JS、CSS、SCSS、HTML、PNG 文件命名

  - 全部采用小写方式， 以中划线分隔

  - render-dom.js / signup.css / index.html / company-logo.png
  - 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式

## HTML 规范

#### **标签**

- 自闭合（self-closing）标签，无需闭合 ( 例如： `img` `input` `br` `hr` 等 )
- HTML5 中新增很多语义化标签，所以优先使用语义化标签，避免一个页面都是 div 或者 p 标签

- 使用双引号(“ “) 而不是单引号(‘ ‘)
- 尽量减少标签数量

#### **嵌套**

- <a>不允许嵌套 <div> 这种约束属于语义嵌套约束，严格嵌套约束在所有的浏览器下都不被允许

- `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等;

- `p>`里不可以嵌套块级元素，`<div>、<h1>~<h6>、<p>、<ul>/<ol>/<li>、<dl>/<dt>/<dd>、<form>`

## CSS 规范

#### 命名

- 类名使用小写字母，以中划线分隔 **.fw-800**，尽量使用缩写属性，保证缩写后还能较为清晰保持原单词所能表述的意思

- 不允许使用拼音，但是可以使用业界熟知的或者约定俗成的。命名使用英文，禁止使用特殊字符

- id 采用驼峰式命名，

- scss 中的变量、函数、混合、placeholder 采用驼峰式命名

- class、id 都需小写、样式名不能包含`ad`、`guanggao`、`ads`、`gg`是广告含义的关键词，避免元素被网页拓展、插件屏蔽

- 名称间隔使用`-`符号

- 类名命名需要语义化，参考下面的示例：

  ```
   .wrap{}                 //外层容器
   .mod-box{}              //模块容器
   .btn-start{}            //开始
   .btn-download-ios{}     //ios下载
   .btn-download-andriod{} //安卓下载
   .btn-head-nav1{}        //头部导航链接1
   .btn-news-more{}        //更多新闻
   .btn-play{}             //播放视频
   .btn-ico{}              //按钮ico
   .btn-lottery{}          //开始抽奖
   .side-nav{}             //侧栏导航
   .side-nav-btn1{}        //侧栏导航-链接1
   .btn-more{}             //更多
  ```

#### 前缀规范

- g- 全局通用样式命名，前缀 g 全称为 global，一旦修改将影响全站样式
- m- 模块命名方式
- ui- 组件命名方式
- js- 所有用于纯交互的命名，不涉及任何样式规则

#### 简写/省略/缩写

- 省略 0 开头小数点前面的 0、省略 0 后面的单位
- 省略 URI 外的引号

#### 选择器

- 子选择器`（ul < li）`
- 相邻选择器`（h1+p）`
- 伪类选择器`（a:hover, li:nth-child）`
- **避免使用通用选择器、**子选择器
- **避免使用多层标签选择器。** 使用 class 选择器替换，减少 CSS 查找
- **使用继承** `#bookmarkMenuItem > .menu-left { list-style-image: url(blah) }`

#### 正确使用 Display 的属性

- display: inline 后不应该再使用 width、height、margin、padding 以及 float；
- display: inline-block 后不应该再使用 float；
- display: block 后不应该再使用 vertical-align；

## JavaScript 规范

#### 命名

- 采用小写驼峰命名 `lowerCamelCase，`代码中的命名均不能以下划线，也不能以下划线或美元符号结束

- **方法名、参数名、成员变量、局部变量** 都统一使用 `lowerCamelCase` 风格，必须遵从**驼峰形式**。
  ` let loadingModules = {};`

- 其中 `method` 方法命名必须是 **_动词_** 或者 **_动词+名词_** 形式

- **常量 ** 命名全部大写，单词间用下划线隔开 **_MAX_STOCK_COUNT_** `let MAXCOUNT = 10;`

- **枚举变量** 使用 `Pascal` 命名法 **枚举的属性**， 使用全部字母大写，单词间下划线分隔的命名方式。

  ```js
  let TargetState = {
    READING: 1,
    READED: 2,
    APPLIED: 3,
    READY: 4,
  };
  ```

- **boolean** 类型的变量使用 is 或 has 开头。

  ```js
  let isReady = false;
  let hasMoreCommands = false;
  ```

- `类` 使用 `Pascal命名法`。

  ```js
  function TextNode(options) {}
  ```

- 函数方法常用的动词

  ```
    get 获取/set 设置		add 增加/remove 删除 	create 创建/destory 移除	start 启动/stop 停止
    open 打开/close 关闭		load 载入/save 保存,	begin 开始/end 结束,	edit 编辑/modify 修改,
    select 选取/mark 标记		insert 插入/delete 移除,  	add 加入/append 添加	clean 清理/clear 清除,
    play 播放/pause 暂停,		send 发送/receive 接收		begin 起始/end 结束,	start 开始/finish 完成
    enter 进入/exit 退出,		abort 放弃/quit 离开
  ```

#### 注意

- 如无必要，勿增注释，尽量提高代码本身的清晰性、可读性。合理的注释、空行排版等，可以让代码更易阅读、更具美感

- 统一使用单引号(‘)，不使用双引号(“)。这在创建 HTML 字符串非常有好处：

- 不同逻辑、不同语义、不同业务的代码之间插入一个空行分隔开来以提升可读性。

- 必须优先使用 ES6 中新增的语法糖和函数。这将简化你的程序

- 远不要直接使用 undefined 进行变量判断；使用 typeOf 和字符串 'undefined' 对变量进行判断。

  ```js
  if (typeof person === 'undefined') {
    ...
  }
  ```

#### 空格

- 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

- 用作代码块起始的左花括号 `{` 前必须有一个空格。

- `f / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格。

- 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。

- 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。

  ```js
  function funcName() {}
  ```

- `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格。

- 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。

  ```js
  callFunc(param1, param2, param3);

  save(this.list[this.indexes[i]]);

  needIncream && (variable += increament);

  if (num > list.length) {
  }
  ```

- 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。

  ```js
  var arr1 = [];
  var arr2 = [1, 2, 3];
  var obj1 = {};
  var obj2 = { name: "obj" };
  var obj3 = {
    name: "obj",
    age: 20,
    sex: 1,
  };
  ```

- 行尾不得有多余的空格。

#### 换行

- 每个独立语句结束后必须换行。

- 运算符处换行时，运算符必须在新行的行首。

  ```js
  if (
    (user.isAuthenticated() &&
      user.isInRole("admin") &&
      user.hasAuthority("add-admin")) ||
    user.hasAuthority("delete-admin")
  )
    var result = number1 + number2 + number3 + number4 + number5;
  ```

- 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。所有参数必须增加一个缩进。

  ```js
  foo(aVeryVeryLongArgument, anotherVeryLongArgument, callback);
  ```

#### 二元和三元操作符

- 操作符始终写在前一行, 以免分号的隐式插入产生预想不到的问题。

  ```js
  let x = a ? b : c;
  let y = a ? longButSimpleOperandB : longButSimpleOperandC;
  let z = a ? moreComplicatedB : moreComplicatedC;
  ```

- 三元操作符用于替代 if 条件判断语句。

  ```js
  // Not recommended
  if (val != 0) {
    return foo();
  } else {
    return bar();
  }
  // Recommended
  return val ? foo() : bar();
  ```

### 注释

- 单行注释，必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。

- 多行注释 有多行注释内容时，使用多个单行注释。

- 文件注释、文件顶部必须包含文件注释，用 `@file` 标识文件说明。

  ```js
  /**
   * @file Describe the file
   */
  ```

- 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。

#### 函数设计

- 函数设计基本原则：低耦合，高内聚 （一旦你修改其中一个函数，其他 49 个函数都需要做修改，这就是高耦合的后果）
- [建议] 一个函数的长度控制在 50 行以内 过多的逻辑单元混在一个大函数中，易导致难以维护。
- 复杂的操作应进一步抽取，通过函数的调用来体现流程
- 特定算法等不可分割的逻辑允许例外

#### 函数和变量

- 同一个函数内部，局部变量的声明必须置于顶端 因为即使放到中间 JS 解析器也会提升至顶部

- 对于性能有高要求的场合，建议存在一个空函数的常量，供多处使用共享。

  ```js
  var EMPTY_INIT = function () {};
  function myClass() {}
  myClass.prototype.aa = EMPTY_INIT;
  myClass.prototype.bb = PTY_INIT;
  ```

#### 性能优化

- 避免不必要的 DOM 操作，浏览器遍历 DOM 元素的代价是昂贵的
- 当一个元素出现多次时，将它保存在一个变量中，就避免多次查询 DOM 树了
- 不要扩充内置原型（虽然给 Object(), Function()之类的内置原型增加属性和方法很巧妙，但是会破坏可维护性）
- 不要用隐含的类型转换，用 parseInt() 进行数字转换
- 不要用 with，continue 语句

#### 执行优化

- 改变页面视觉习性的脚本绝对要首先执行。
- 页面内容初始化

## 移动端页面设计规范

#### 页面尺寸

- 移动端设备屏幕尺寸非常多，为了适配不同设备，推荐使用`iPhoneX`的屏幕比例作为基准
- 尺寸大小：`750x1624px`，同时需保证重要内容在安全区域内，尺寸大小：`646x1206px`

#### 移动端设计稿推荐设计尺寸：`750x1624px，`重要内容在安全区域内：`646x1206px`

- 市面上的机型超过 65%的长宽比为`178:100`，如果按照设计 app 的思路，只需要选取一个中间设备`iPhone 6`尺寸来适配即可，但我们发现微信/手 Q 的浏览器头部并不是按照等比来缩放的，所以如果设计稿按照`iPhone 6`尺寸来等比例放大到`iPhone 6 plus`上，会出现留有一条黑边
- 首屏范围的设定选取的主流机型`iPhone 6`的分辨率大小，安全宽高为向下兼容到`iphone5s`的尺寸。

#### 标题文字

- 主标题建议在 7 个字内，一行最多不超过 7 字，标题一般是经过设计的字体
- 标题文字超过 7 个字的情况下，文字折行处理，并且加强重要词语
- 副标题文字需要能够说明详细活动信息，字体建议在 24-40 号之间

#### 正文标题与内容

- 标题：字号 48，使用粗体
- 正文：字号 30 点，使用常规体
- 引文和次要信息：字号 24
- 段首无需空格，左对齐即可

#### 文章列表的字号与间距

- 文章的标题不宜过长，建议控制在 18 字内
- 文章列表的间距需不得小于 90px
- 字号建议用 26~30 号

#### 按钮

- 页面只有一个按钮时候，按钮居中对齐，按钮高度需要大于 80px
- 如果按钮的重要级相当，建议用左右布局；不一致则建议用上下布局

#### 图标

- 热区大小 最小面积：44x44 像素(底部导航栏)
- 图形大小 最小面积：30x30 像素
