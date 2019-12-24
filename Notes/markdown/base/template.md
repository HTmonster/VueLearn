#### 模版语法简介
- 基于`HTML`的模版语法
- 虚拟DOM
- 可以使用可选的JSX

#### 插值
1. 文本 【双大括号】
```
 //属性的值改变时候会对应的进行改变
 <h1>{{msg}}</h1>
 
 // v-once指令 一次性插值
 <span v-once>不会改变{{msg}}</span>
```
2. 原始HTML 【使用v-html】
```
<span v-html="rawHtml"></span>
```
3. HTML特性 【使用v-bind】
```
<div v-bind:id="dynamicID"></div>
<button v-bind:disabled="isButtonDisabled">Button</button>
```

- 绑定的时候可以使用JavaScript表达式
```
//限制 每个绑定只能包含单个表达式
{{number+1}}
{{ok? 'YES':'NO'}}
{{message.split('').reverse().join('')}}
<div v-bind:id="'list-'+id"></div>
```

#### 指令
> 指令是带有`v-`前缀的特殊特性 指令在表达式的值改变的时候将其产生的影响响应式的作用于DOM

1. 参数 （有些指令可以接收参数）
```
//v-bind: 响应式更新HTML特性 
<div v-bind:href="url"></div>//将href特性与表达式url的值绑定

//v-on: 监听DOM事件
<div v-on:click="doClick"></div>//在Click之后做doClick函数
```
2. 动态参数
==2.6.0新增==
```
//使用方括号括起来的JavaScript表达式作为一个指令的参数

<a v-bind:[attributeName]="url"></a>
<a v-on:[eventName]="doSomething"></a>

//值约束: 参数预期会求出一个字符串 异常情况下为 `null`
//表达式约束: 某些空格 引号无效
```

3. 修饰符
```
// . 指明的特殊后缀 用于指出一个指令应该以特殊的方式绑定
<form v-on:submit.prevnet="onSubmit"></form>//.prevent 修饰符告诉v-on指令对于触发的时间调用 event.preventDefualt()
```
#### 缩写
1. `v-bind`
```
<!-- 完整语法 -->
<a v-bind:href="url">...</a>

<!-- 缩写 -->
<a :href="url">...</a>
```
2. `v-on`
```
<!-- 完整语法 -->
<a v-on:click="doSomething">...</a>

<!-- 缩写 -->
<a @click="doSomething">...</a>
```


