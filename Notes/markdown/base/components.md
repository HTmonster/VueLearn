### 组件学习

#### 定义方式与使用
##### 组件定义
```js

    /*定义一个组件  参数1：组件名字*/
    Vue.component('button-counter',{
        data: function(){
            return {
                count:0
            }
        },
        template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
    })

```
- 参数一：组件的名字
- data段必须是**函数**
    - 因此每个实例可以维护一份返回对象的拷贝（互不影响）

##### 组件使用
```html
<div id="app">
    <button-counter></button-counter>
    <button-counter></button-counter>
</div>
```
- 组件可以复用

#### 组件的组织
> 以一个嵌套的组件树的形式总结

#### 组件的注册

|注册对比|全局注册|局部注册|
|-------|-------|--------|
|注册方法|Vue.component()|通过一个普通的js对象来定义 var component={}|
|使用方法|在任何新创建的组件中使用|在组件的**components**选项中定义|

#### props向子组件传递数据
- `props`选项定义要传递的值
-  在组件中传递值
```js

    //使用props传递数据
    Vue.component('props-component', {
        props: ['props_value'],
        template: '<div>I\'m component use props. This is props value:{{props_value}}</div>'
    })
```
```html
<!-- props传递参数-->
    <br><h4>3. 组件使用props传递数据</h4>
    <props-component title="My journey with Vue"></props-component>
```

#### 监听子组件
- 子组件使用内建的`emit`来触发事件

```js
    /*监听子组件*/
    Vue.component('event-listen', {
        template: `
            <div >
                <button v-on:click="$emit('enlarge-text')">
                    Enlarge text
                </button>
                <p>font</p>
            </div>
        `
    })


    new Vue({
        el: '#events-demo',
        data: {
            FontSize: 1
        }
    })
```
```HTML
    <!-- 监听子组件-->
    <br><h4>4. 监听子组件</h4>
    <div id="events-demo">
        <div :style="{ fontSize: FontSize + 'em' }">
            <event-listen
            v-on:enlarge-text="FontSize += 0.1"
            ></event-listen>
        </div>
    </div>
```
- 事件值的传递：子组件`$emit`函数传递参数 父组件使用`$event`来接收值
```html
    <button v-on:click="$emit('enlarge-text','0.1'")></button>
```
```javascript
    <event-listen
    v-on:enlarge-text="FontSize += $event"
    ></event-listen>
```
- 组件使用`v-model`
```html
   <!--支持自定义输入组件-->
   <input v-model="searchText">
   <!--等价于-->
   <input v-bind:value="searchText"
          v-on:input="searchText=$event.target.value"
   >
```
使其能够正常工作
```javascript
    Vue.component('test-input',{
        props:['value'],
        template:`
        <input
            //将value特性绑定到一个叫value的props的特性中
            v-bind:value="value" 
            //input事件触发时候，新的值通过自定义input时间抛出
            v-on:input="$emit('input',$event.target.value)"
        `
    })

    <test-input v-model="searchText"></test-input>
```
