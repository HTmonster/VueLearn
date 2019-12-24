#### 创建实例
> 通过`Vue`函数创建新的实例

- 创建时候可以传入**选项对象**

```
var vm=new Vue({
    //选项
})
```

#### 数据与方法
- 将`data`对象中的所有属性加入到**响应系统**中
- 数据改变时候，视图会重新渲染
    - 只有当创建实例时候就++存在++的属性才是**响应式**的
- 使用`Object.freeze()` 可以阻止修改现有的属性

##### 实例属性和方法
```
var data={a:1}
var vm = new Vue({
    el:'#example',
    data:data
})

// data实例属性
vm.$data===data //true
// el实例属性
vm.$el=== document.getElementById('example')//true
// watch实例方法
vm.$watch('a',function(newValue,oldValue){
    //回调在 vm.a改变时候调用
}
```
#### 实例生命周期钩子

==不要在选项属性或回调上使用箭头函数 (this的关系)==
![生命周期图](https://cn.vuejs.org/images/lifecycle.png)
**例子**. 实例被创建之后 `created` 钩子
```
var vm=new Vue({
    data:{
        a:1
    },
    created:function(){
        console.log('a is:'+this.a) //a is 1
    }
})
```




