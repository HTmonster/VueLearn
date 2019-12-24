#### `v-for`数组对应一组元素
```
//使用 v-for 渲染数组为一组元素
<ul id="example">
    <li v-for="(item,index) in items">  //可以使用 of 代替 in
        {{item.message}}//项目元素
        {{index}} //索引
        {{parrentMessage}} //父级元素
    </li>
</ul>
```
```
var vm=new Vue({
    el:"#example",
    data:{
        parrentMessage:"parent",
        items:[
            {message:'1'},
            {message:'2'}
        ]
    }
})
```
#### `v-for`遍历对象  根据==object.kys()==
```
<div id="example">
    <li v-for="(value,name,index) in object">
        {{ value }} //值
        {{ name }}  //属性名
        {{ index }} //索引
    </li>
</div>
```
#### 维护状态
**问题**:就地更新策略
**解决办法**: key
```
<div v-for="item  in items" v-bind:key="item.id">
    <!-- 内容 -->
</div>
```
#### 更新状态检测
1.变异方法 
>变异方法进行了包裹,会触发视图更新 
 - push()
 - pop()
 - shift()
 - unshift()
 - splice()
 - sort()
 - reverse()
2. 替换数组
> 非变异方法 不改变数组 返回一个新数组
 - filter()
 - concat()
 - slice()
3. 注意事项
```
//1. 不能检测 利用索引设置数组
vm.items[indexOFItem] = newValue
//替换方法：使用Vue.set
Vue.set(vm.items,indexOfItem,newValue)

//2.不能检测修改数组长度
vm.items.length=newLength
//替换方法：使用splice
vm.items.splice(indexOfItem,1,newLength)
```

#### 对象变更注意事项
```
//不能检测对象属性的添加与删除
var vm=new Vue({
    data:{
        userProfile:{
            name:"htmonster"
        }
    }
})

// 添加元素的替换方法
Vue.set(vm.userProfile,'age',21)//全局方法
vue.$set(vm.userProfile,'age',21)//实例方法

// 添加多个对象属性
vm.userProfile=Object.assgin({},vm.userProfile,{age:27,job:'jc'})
``` 
#### 显示过滤/排序后的结果
```
<li v-for="n in evenNumbers">{{n}}</li>//使用计算属性
<li v-for="n in even(numbers)">{{n}}</li>//使用方法
```

```

data:{
    numbers:[1,2,3,4,5]
},
//使用计算属性
computed:{
    evenNumber:function(){
        return this.numbers.filter(function(number){
            return number%2===0
        })
    }
},
//使用方法 
methods:{
    even:function(numbers){
        return numbers.filter(function(number){
            return number%2===0
        }
    }
}
```
#### 值范围
```
//接受整数 将模版重复到对应次数
<div>
    <span v-for:"n in 10">{{n}}</span>//1 2 3 4 5 6 7 8 9 10
</div>
```
#### 在<template>中使用v-for
```
//使用template渲染多个数据
<ul>
  <template v-for="item in items">
    <li>{{ item.msg }}</li>
    <li class="divider" role="presentation"></li>
  </template>
</ul>
```
#### v-for与 v-if
- v-for 优先级高于 v-if


