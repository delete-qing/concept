# 前端开发需要注意事项

### 命名规范

##### 项目命名

1.  全部采用小写方式， 以中划线分隔。 mall-management-system

##### 目录命名

1. 全部采用小写方式， 以中划线分隔，有复数结构时，要采用复数命名法， 缩写不用复数
   - scripts / styles / components / images / utils / layouts / demo-styles / demo-scripts / img / doc
2. 使用 kebab-case 命名

   - head-search / page-loading / authorized / notice-icon

3. JS、CSS、SCSS、HTML、PNG 文件命名

   - 全部采用小写方式， 以中划线分隔
   - render-dom.js / signup.css / index.html / company-logo.png

4. 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式

### HTML 规范

1. HTML5 中新增很多语义化标签，所以优先使用语义化标签，避免一个页面都是 div 或者 p 标签

2. 使用双引号(“ “) 而不是单引号(‘ ‘)

### CSS 规范

1. 尽量使用缩写属性

2. 省略 0 后面的单位

##### 命名

1. 类名使用小写字母，以中划线分隔 **.fw-800**

2. id 采用驼峰式命名

3. scss 中的变量、函数、混合、placeholder 采用驼峰式命名

### Javascript 规范

##### 命名

1. 采用小写驼峰命名 lowerCamelCase，代码中的命名均不能以下划线，也不能以下划线或美元符号结束

2. 方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。
   **_localValue / getHttpMessage() / inputUserId_**

3. 其中 method 方法命名必须是 **_动词_** 或者 **_动词+名词_** 形式 **_saveShopCarData /openShopCarInfoDialog_**

4. 函数方法常用的动词

```
get 获取/set 设置,
add 增加/remove 删除
create 创建/destory 移除
start 启动/stop 停止
open 打开/close 关闭,
load 载入/save 保存,
create 创建/destroy 销毁
begin 开始/end 结束,
edit 编辑/modify 修改,
select 选取/mark 标记
undo 撤销/redo 重做
insert 插入/delete 移除,
add 加入/append 添加
clean 清理/clear 清除,
increase 增加/decrease 减少
play 播放/pause 暂停,
connect 连接/disconnect 断开,
send 发送/receive 接收
submit 提交/commit 交付
begin 起始/end 结束,
start 开始/finish 完成
enter 进入/exit 退出,
abort 放弃/quit 离开
obsolete 废弃/depreciate 废旧,
```

5. 常量命名全部大写，单词间用下划线隔开 **_MAX_STOCK_COUNT_**

##### js 其他

1. 不同逻辑、不同语义、不同业务的代码之间插入一个空行分隔开来以提升可读性。

2. 统一使用单引号(‘)，不使用双引号(“)。这在创建 HTML 字符串非常有好处：

3. 必须优先使用 ES6,ES7 中新增的语法糖和函数。这将简化你的程序，必须强制使用 ES6, ES7 的新语法，比如箭头函数、await/async，解构，let，for…of 等等

4. 远不要直接使用 undefined 进行变量判断；使用 typeof 和字符串 'undefined' 对变量进行判断。

```js
if (typeof person === 'undefined') {
    ...
}
```
