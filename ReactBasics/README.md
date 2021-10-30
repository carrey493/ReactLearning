# React基础知识学习

## 第一章：React入门

### 1.1Reacr简介

#### 1.1.1官网

- 英文官网: https://reactjs.org
- 中文官网: https://react.docschina.org/

#### 1.1.2介绍描述

- 用于动态构建用户界面的JavaScript库(只关注于视图)
- 由Facebook开源

#### 1.1.3React特点

- 声明式编码
- 组件化编码
- React Native编写原生应用
- 高效〈优秀的 Diffing 算法）

#### 1.1.4.React高效的原因

- 使用虚拟(virtual)DOM,不总是直接操作页面真实DOM。
- DOM Diffing 算法,最小化页面重绘。

### 1.2React的基本使用

#### 1.2.1Hello React

```html
<div id="test"><h1 id="title"><span>Hello React</span></h1></div>
```

#### 1.2.2相关js库

- eact.js: React核心库。
- react-dom.js:提供操作 DOM的react扩展库。
- babel.min.js:解析SX语法代码转为S代码的库。

#### 1.2.3创建虚拟DOM的两种方式

- 纯js方式（一般不用）

```js
/ 1.创建虚拟DOM
// const VDOM = React.createElement(标签名,标签属性,标签内容)
const VDOM = React.createElement('h1',{id:'title'},'hello react')
// 2.创建虚拟DOM到页面
//ReactDOM.render(虚拟DOM,容器)
ReactDOM.render(VDOM,document.getElementById('test'))
```

- jsx方式

```jsx
// 1.创建虚拟DOM
const VDOM = <h1>Hello React</h1> //此处一定不要写引号，因为不是字符串
// 2.创建虚拟DOM到页面
//ReactDOM.render(虚拟DOM,容器)
ReactDOM.render(VDOM,document.getElementById('test'))
```

#### 1.2.4虚拟DOM与真实DOM

- 1.本质是object类型的对象（一般对象）
- 2.虚拟DOM比较轻，真实DOM比较重，因为虚拟DOM是在React内部在用，无需真实DOM上那么多属性。
- 3.虚拟DOM最终会被React转化为真真实DOM,呈现在页面上

### 1.3React JSX

#### 1.3.1效果

```html
<div id="test"><h1 id="title"><span>Hello React</span></h1></div>
```

#### 1.3.2JSX

- 全称:JavaScript XML
- react 定义的一种类似于XML的JS扩展语法: JS + XML
- 本质是React.createElement(component, props, ...children)方法的语法糖
- 作用:用来简化创建虚拟DOM
  - a.写法:var ele = <h1  Hello JSX!  </h1
  - b.注意1:它不是字符串,也不是HTML/XML标签
  - c.注意2:它最终产生的就是一个JS对象
- 标签名任意:HTML标签或其它标签

#### 1.3.3渲染DOM与真实DOM

- jsx语法规则：

- 1.定义虚拟DOM时，不要写引号。

- 2.标签中混入js表达式中使用{}。

- 3.样式的类名指定不要用class,要用className.

- 4.内联样式,要用style={{key:value}}的形式去写

- 5.虚拟DOM必须只有一个根标签

- 6.标签必须闭合

- 7.标签首字母
  - (1).若以小写字母开头，则将标签转为html中的同名元素，若html中无标签对应的同名元素，则报错。

  - (2).若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错。

#### 1.3.4JSX练习

- 需求：动态展示列表

```jsx
const VDOM = (
    <div>
        <h2>
            前端js框架列表
        </h2>
        <ul>
            {
                data.map((item,index)=>{
                    return <li key={index}>{item}</li>
                })
            }
        </ul>
    </div>
)
```

### 1.4模块与组件、模块化与组件化的理解

#### 1.4.1模块

- 理解：向外提供特定功能dejs程序，一般就是一个js文件。
- 为什么要拆成模块：随着业务逻辑的增加，代码越多越复杂。
- 作用：复用js，简化js的编写，提高js运行效率

#### 1.4.2组件

- 理解：用来实现局部功能效果的代码和资源的集合(html/css/js/image 等等)
- 为什么：一个界面的功能更复杂
- 作用：复用编码，简化项目程序，提高运行效率

#### 1.4.3模块化

- 当应用的js都以模块来编写的，这个应用就是一个模块化应用

#### 1.4.4组件化

- 当应用是以多组件的方式实现时，这个应用就是一个组件化应用

## 第二章：React面向组件编程

### 2.1基本理解与使用

#### 2.1.1使用React开发者工具调试

- React Developer Tools

#### 2.1.2效果

- 函数式组件：适用于【简单组件】的定义
- 类式组件：适用于【复杂组件】的定义