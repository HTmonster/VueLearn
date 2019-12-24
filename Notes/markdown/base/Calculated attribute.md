#### 计算属性
> 模版内的表达式便利，但是只适合用于简单运算。对于复杂逻辑应该使用**计算属性**

**例子**
```html
<div id="Example">
    <p>Original message: {{message}}</p>
    <p>Reversed message: {{reversedMessage}}</p>
</div>
```

```javascript
var vm=new Vue({
    el:"#Example",
    data:{
        message:"hello"
    },
    computed:{
        //计算属性的getter
        //声明了一个计算属性 提供的函数将用作reversedMessage的getter函数
        reversedMessage:function(){
            retrun this.message.split('').reverse().join('')
        }
    }
})
```
1. 计算属性与**方法**对比
```html
<!-- 在表达式中调用方法 -->
<p> Reversed message:"{{reversedMessage()}}"</p> 
```
```javascript
var vm=new Vue({
    el:"xxx",
    data:{
        xxxx
    },
    
    //定义为方法
    methods:{
        reversedMessage: function () {
            return this.message.split('').reverse().join('')
        }
    }
})
```

对比|计算属性 | 方法
--|---|---
更新原理|响应式依赖缓存 | 无缓存
更新时机|相关响应式依赖发生改变|重新渲染时

2. 计算属性与**侦听属性**对比
> **侦听属性**:通用的方式来++观察++和++响应++实例上的数据变动
```html
<div id="demo">{{fullname}}</div>
```
```javascript
var vm= new Vue({
    el:"#demo",
    data:{
        firstName:'Foo',
        lastName:'Bar',
        fullName:'Foo Bar'
    },
    //使用计算属性
    computed:{
      fullName:function(){
          return this.firstName+" "+this.lastName
      }  
    },
    // 使用侦听属性  
    watch:{
        firstName:function(val){
            this.fullName = val +' '+this.lastName
        },
        lastName:function(val){
            this.fullName=this.firstName+" "+val
        }
    }
})
```
对比|计算属性|侦听属性
---|---|--
范式|声明式|命令式
构造|简单|复杂 重复
3. 计算属性的**Setter**
>计算属性只有 getter 但是必须的时候可以提供setter
```javascript
computed:{
    fullName:{
        //getter
        get:function(){
            return this.firestName+' '+this.lastName
        }
        //setter
        set:function(){
            var names=newValue.split(' ')
            this.firstName=names[0]
            this.lastName=name[1]
        }
    }
}
```
#### 侦听器
- 通过`watch`选项提供一个通用的方法 来++响应++数据变化
- **适用于** 数据变化时候 需要 ++异步操作++和++开销较大++的操作
**例子**
```html
<div id="watch-example">
    <p>
</div>
```