

https://reactjs.org/

https://draftjs.org Rich Text Editor Framework for React

https://www.gatsbyjs.com/ Gatsby

https://nextjs.org/


# React

React是用于构建用户界面的JavaScript库

react.min.js React 的核心库
react-dom.min.js 提供与 DOM 相关的功能
babel.min.js Babel可以将 ES6 代码转为 ES5 代码，这样我们就能在目前不支持  ES6 浏览器上执行 React 代码。Babel 内嵌了对 JSX 的支持。通过将 Babel 和 babel-sublime  包（package）一同使用可以让源码的语法渲染上升到一个全新的水平。
Copyright (c) Facebook Inc.


辅助开发工具: Webpack Babel ESLint





```html
<!-- react是用来创建元素的, react-dom是用来渲染页面的, 两者搭配使用更好 -->
<!--CDN-->
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<!-- 生产环境中不建议使用 -->
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
注意: 在浏览器中使用 Babel 来编译 JSX 效率是非常低的

<!-- npm安装  -->
npm i react react-dom
<script src="./node_modules/react/umd/react.development.js"></script>
<script src="./node_modules/react-dom/umd/react-dom.development.js"></script>
    



```



```html
<!-- React元素的渲染 -->
<div id="root"></div>
<script>
    // React.createElement('元素名称','元素属性','元素的子节点','子节点'....)
    const hello = React.createElement('h1',{name:'title',id:'id'},'Hello',' React');
    //ReactDOM.render(要渲染的react元素, DOM对象 挂载点); 
    ReactDOM.render(hello, document.getElementById('root'));


</script>
```





# React脚手架



```html
<!-- npx 脚手架的名称(不可变) 项目名称(可变) -->
npx create-react-app my-app
cd my-app
npm start

<!-- 也能创建react脚手架 -->
npm init react-app my-app
yarn create react-app my-app
yarn是Facebook发布的包管理器，可以看作是npm的替代品，功能与npm相同

```


```js
//导入react包
import React from 'react';
import ReactDOM from 'react-dom/client';

```



# JSX
JSX是JavaScript XML的简写，表示在JavaScript代码中写XML(HTML)格式的代码，是react声明式的体现
JSX是ECMAScript的语法扩展
JSX语法只有在脚手架使用，浏览器中使用需要babel编译处理之后才能使用
编译JSX语法的包为: @bable/preset-react

React完全利用JS语言自身的能力来编写UI，而不是造轮子增强HTML功能(VUE中有很多指令和插值表达式来增强HTML功能，而React仅仅使用js自身的语法)

```js
<!-- JSX写法更简洁 -->
<script>
// React写法比较繁琐
const table = React.createElement('div',{className: 'shopping-list'},
    React.createElement('h1', null, 'Shopping List'),
    React.createElement('ul',null,
        React.createElement('li', null, 'Instagram'),
        React.createElement('li', null, 'WhatsApp')))
ReactDOM.render(table, document.getElementById('root'));
ReactDOM.render(table, 'root');// 简写形式
</script>


const list = <div class="shopping-list">
    <h1>Shopping List</h1>
    <ul><li>Instagram</li><li>WhatsApp</li></ul>
</div>

// 属性名使用驼峰命名法
// class属性写成className,for属性写成htmlFor,tabindex写成tabIndex
// 没有子节点的元素用闭合标签
const h2 = <h1 className='title'>Hello<span /></h1>

// 推荐使用小括号包裹元素,多行分割, 避免分号,但是不强制使用
const h1 =(<h1>Hello JSX</h1>)

// 嵌入JavaScript表达式{}
const name = 'JSX';
const div = (<h1>Hello {name}</h1>)//嵌入值

let isLoading = false
let name = () => {return isLoading ?"加载中":"加载完成"}
let name = ()=>{return isLoading && "加载中"}//没有加载完显示字符，加载完为空字符
const div = (<h1>{name()}</h1>)//嵌入函数

// 列表渲染，使用map渲染方法，key的属性值保证唯一，给map遍历的数据添加属性
const songs = [{id: 1, name: '歌曲1'}, {id: 2, name: '歌曲2'}, {id: 3, name: '歌曲3'}]
const div = (<ul>{songs.map(item => <li key={item.id}>{item.name}</li>)}</ul>)//遍历循环

// 添加行内样式，js表达式里放着是一个对象
const h1 = <h1 style={{color:'red',backgroundColor:'gray'}}>JSX</h1>

// 引入外部样式
//index.css: .title {text-align: center; color: red; background-color:gray;}
import './index.css';
const h1 = <h1 className={'title'}>JSX</h1>

```


# React组件

React的一等公民, 使用React就是在用组件，组件表示页面中的部分功能，页面由多个组件组合而成，组件独立，可复用，可组合


```js

```

































