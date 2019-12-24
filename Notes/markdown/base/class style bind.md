#### 绑定HTML Class
1. 对象语法
```
//给class传递一个对象  动态的切换class
<div v-bind:class="{active:isActive}"></div> //active存在与否取决于 isActive

<div class="static" v-bind:class="{ active: isActive,'text-danger':hasError}"></div> //当根据两个属性动态变化
// isActive=true  hasError=false  =>  static active 
// isActive=true  hasError=ture   =>  static active text-danger

//数据对象也可以不必绑定在模版里 绑定Data或者计算属性
<div v-bind:class="classObject"></div>

```

```
// 1.绑定data里的对象
data:{
    classObject:{
        active:true,
        'text-danger':false
    }
}

// 2. 绑定计算属性
data:{
    isActive:true,
    error:null
},
computed:{
    classObject:function(){
        return{
            active:this.isActive&&!this.error,
            'text-danger':this.error&&this.error.type == 'fatal'
        }
    }
}
```
2. 数组语法
```
//把数组传给 v-bind:class 应用一个class列表

<div v-bind:class="[activeClass,errorClass]"></div> //渲染为: class="active text-dannger">

<div v-bind:class="[isActive?activeClass:'',errorClass]"></div>//根据条件切换

<div v-bind:class="[{active:isActive},errorClass]"></div> //使用对象语法
```

```
data:{
    activeClass:'active',
    errorClass:'text-danger'
}
```
3. 用在组件上

- 自定义组件使用 `class` 属性时,class属性添加到元素上时,元素上的class==不会被覆盖==

#### 绑定内联样式
1. 对象语法
```
<div v-bind:style="{color: activeColor,fontSize: fontSize+'px'}></div> " //绑定为JS对象  

<div v-bind:style="styleObject"></div> //直接绑定为一个样式对象
```
```
// 1.绑定data项
data:{
    activeColor:'red',
    fontSize:30
}
// 2.绑定一个样式对象
data:{
    styleObject:{
        color:'red',
        fontSize:'13px'
    }
}
```

2. 数组语法
```
<div v-bind:style="[baseStyles,overridingStyles]"></div>//将多个样式对象应用在同一元素上
```
3. 自动添加前缀
- **浏览器引擎前缀**的CSS属性 自动侦测并添加前缀
4. 多重值 ==2.3.0开始==
```
//可以提供一个包含多个值的数组
<div :style="{display:[''}"
```


