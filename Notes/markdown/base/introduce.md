### 介绍

#### 与其他框架的对比

##### React
###### 共同点
- 都使用了Virtual DOM
- 提供**响应式**和**组件化**的视图组件
- 注意力保持在核心库，其他功能交给相关的库

###### 区别点
 区别 |React | vue 
---|---|---
 渲染速度优化|使用 `pureComponent`或者重写`shouldCompunentUpdate` | 组件的依赖在渲染中自动追踪
 HTML&CSS|所有的都是javascript html用JSX表示 |遵循经典的web结构 使用模版
 作用域内CSS|CSS-in-JS|单文件组件类似style标签
 规模| |向下拓展容易

#### 安装

##### 直接引入
- 最新版本`<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>`
- 生产环境`<script src="https://cdn.jsdelivr.net/npm/vue@2.6.0"></script>`
- 原生ES modules
    ```
    <script type="module">
      import Vue from 'https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.esm.browser.js'
    </script>
    ```
##### NPM安装

#### 声明式渲染
> 采用简洁的模版语法来声明式将数据渲染进DOM系统

#### 条件与循环
##### 条件控制 `v-if`
- 把数据绑定到DOM结构
- 提供过渡效果系统

##### 循环渲染 `v-for`
- 渲染数组数据

#### 处理用户输入
> 用户和应用进行交互

- `v-on`
    - 添加一个事件指令器
- `v-model`
    - 表单输入和应用状态之间的双向绑定

#### 组件化应用构建
- 允许使用小型 独立 可复用的组件构建大型应用
- 组件的本质：一个拥有**预定义选项**的++Vue实例++

##### 注册组件

```
Vue.component('todo-item', {
      props: ['todo'],//父作用域传到子组件
      template: '<li>{{ todo.text }}</li>'
    })
```
