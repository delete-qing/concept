##### 循环

循环map的时候  可以之久循环 不用加（）也是可以的

```js
record.single_products.map(e => <div key={e.id}>{e.name}</div>) 
```

##### 函数的创建

函数的事件的名称 第一个字母必须大写

##### 事件的什么时候加箭头

```js
//首先 必须知道es6中的this指向性问题
	//1. this指向 指的是上下中this 本身是没有this的
	//2. 谁调用就指向谁


//像这种的是  html 和事件都是 不需要箭头函数的  但是这是不改变state的数据的
    getDownloadUrl(){
        //这里有一个默认的属性  事件对象e
        //组织浏览器默认行为  e.preventDefault()
        console.log('000')
    }
	<a style={{ marginLeft: 10 }} onClick={this.getDownloadUrl}>{f.filename}</a>


//加上箭头函数
 getDownloadUrl(){
       this.steState({num:2})
    }
<a style={{ marginLeft: 10 }} onClick={()=>this.getDownloadUrl}>{f.filename}</a>
// 这个this是指render里面的this的
// 但是this.getDownloadUrl调用的是getDownloadUrl 里面的this ，而getDownloadUrl的this是指向state里面的this 所以他能改变state里面的数据


//或者这样用的  原理是一样的  都是改变了this的指向 推荐的是这种的
 getDownloadUrl=()=>{
       this.steState({num:2})
    }
<a style={{ marginLeft: 10 }} onClick={this.getDownloadUrl}>{f.filename}</a>
```

##### 表单（受控组件与非受控组件）

-  受控组件

  在React中，可变状态通常保存在组件的状态属性中，并且只能使用 setState() 进行更新，而表单(输入框)在React不用state也能改变 但是这些数据又要维护在state中，所以给这些输入框了一个value属性来维护在state中，以这种由React控制的输入表单元素而改变其值的方式，称为**受控组件**。
  
- 非受控组件

  非受控组件指的是，表单数据由DOM本身处理。即不受setState()的控制，与传统的HTML表单输入相似，input输入值即显示最新值。 在非受控组件中，可以使用一个ref来从DOM获得表单值。

  ```js
  	//非受控组件取值
  	constructor(props) {
          super()
          //创建ref
          this.tex = React.createRef()
      }
  
      getTex=()=>{
          console.log(this.tex.current.value)
      }
  
      <input ref={this.tex}>
      <button onClick={this.getTex}></button>
  ```

##### 条件渲染（三目）

```js
// 这样判断也是可以的 这是写在render里面的
{
    editId == '' 
        ? ( <Button type="primary">保存</Button> )
        : ( <Button type="primary">返回</Button> )
}
    
// 这是写在state里面的    
   //方法1
   getButton(){
    return  this.state.editId == '' 
        ? ( <Button type="primary">保存</Button> )
        : ( <Button type="primary">返回</Button> )
   }
  	 //方法2
    getButton(){
        if(this.state.editId == '' ){
            return  <Button type="primary">保存</Button>
        }
        return(
            <Button type="primary">返回</Button>  
        ) 
    } 
    
    render (){
        return (
             {this.getButton}
        )  
    }
   

```

##### React题，class中请求应该放在哪个生命周期

- 放在**componentDidMount**，它是在组件已经完全挂载到网页上才会调用被执行，可以保证数据的加载
- 在这方法中调用setState方法，会触发重新渲染
- 不建议放在constructor，constructor是做组件state初绐化工作
- 不建议放在componentWillMount，如果认为在componentWillMount里发起请求能提早获得结果，这种想法其实是错误的，通常componentWillMount比componentDidMount早不了多少微秒，网络上任何一点延迟，这一点差异都可忽略不计。且componentWillMount已过时

##### setState是异步还是同步

有时表现出异步，有时表现出同步：

- `setState`只在合成事件和钩子函数中是“异步”的，在原生事件和`setTimeout` 中都是同步的。
- 合成事件和钩子函数中没法立马拿到更新后的值，形成了所谓的“异步”
- 可以通过第二个参数 `setState(partialState, callback)` 中的`callback`拿到更新后的结果。
- `setState` 的批量更新优化也是建立在“异步”（合成事件、钩子函数）之上的，在原生事件和setTimeout 中不会批量更新
- 如果对同一个值进行多次`setState`，`setState`的批量更新策略会对其进行覆盖，取最后一次的执行
- 如果是同时`setState`多个不同的值，在更新时会对其进行合并批量更新。

##### component和PureComponent区别？

- `Component`是`class`组件的根基，类组件一切始于`Component` ，在`React.Component`的子类中有个必须定义的 render() 函数。
-  `React.Component` 并未实现 `shouldComponentUpdate()`，
- `React.PureComponent` 中以浅层对比 prop 和 state 的方式来实现`shouldComponentUpdate()`。 并减少了跳过必要更新的可能性
- 如果赋予 React 组件相同的 props 和 state，`render()` 函数会渲染相同的内容，那么在某些情况下使用 `React.PureComponent` 可提高性能。

注意
`React.PureComponent` 中的 `shouldComponentUpdate()` 仅作对象的浅层比较。如果对象中包含复杂的数据结构，则有可能因为无法检查深层的差别，产生错误的比对结果。仅在你的 props 和 state 较为简单时，才使用 `React.PureComponent`，或者在深层数据结构发生变化时调用 `forceUpdate()` 来确保组件被正确地更。
此外，`React.PureComponent` 中的 `shouldComponentUpdate()` 将跳过所有子组件树的 prop 更新。因此，请确保所有子组件也都是“纯”的组件。



##### useMemo与useCallback区别？

`useMemo` 和 `useCallback` 接收的参数都是一样,第一个参数为回调 第二个参数为要依赖的数据

- `依赖数据` 发生变化, 才会重新计算结果，起到缓存的作用
- `useMemo` 计算结果是 `return` 回来的值, 主要用于 缓存计算结果的值 ，应用场景如： 需要 计算的状态
- `useCallback` 计算结果是 `函数`, 主要用于 缓存函数，应用场景如: 需要缓存的函数，因为函数式组件每次任何一个 state 的变化 整个组件 都会被重新刷新，一些函数是没有必要被重新刷新的，此时就应该缓存起来，提高性能，和减少资源浪费。

##### 在React中不是必须要使用JSX的。

 因为其实 JSX 元素只是调用` React.createElement(component, props, ...children)` 的语法糖。其本质还是JavaScript，所有的JSX语法最终都会被转换成对这个方法的调用。因此，使用 JSX 可以完成的任何事情都可以通过纯 JavaScript 完成。
 同时，浏览器是不能直接读取JSX，为了使浏览器能够读取JSX，需要在项目构建环境中配置有关 JSX 编译。比如 让 Babel 这样的 JSX 转换器将 JSX语句 转换为 目标 js 代码，再将其传给浏览器，JS引擎才能成功执行语句。

