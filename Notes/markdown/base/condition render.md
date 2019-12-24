#### `v-if`条件渲染某一块内容

1. 渲染分组 `<template>` 
> 当想切换多个元素的时候 使用 `<template>`元素当做不可见的包裹元素
```
<template v-if="ok">
    <h1>xxx</h1>
    <p>xxxx</p>
    <p>xxxxx</p>
</template>
```
2. else块 `v-else`
```
<div v-if="ok"> I'm if div </div>
<div v-else> I'm else div </div>
```

3. else-if 块  ==2.1.0==
```
<div v-if="type==='A">I'm if div </div>
<div v-else-if="type==='B"> I'm else-if div B </div>
<div v-else-if="type===C"> I'm else-if div C </div>
<div else> I'm else div</div
```

4. 使用`key`管理可复用的元素
> 尽可能的高效渲染元素 复用  使用key来管理(辨别而不进行复用)
```
<template v-if="loginType==='username'">
    <label> UserName</lable>
    <input key="userName-input" placeholder="Enter your name">
</template>
<template v-else-if="loginType==='email'">
    <label> E-mail </lable>
    <input key="email" placeholder="Enter your email">
</template>
```

#### `v-show` 根据条件 展示元素
```
<div v-show="ok"> I'm v-show div </div>
```

#### 对比
对比|v-if|v-show
----|----|------
原理|修改DOM 元素 渲染|修改 display属性
开销|高|低
初始渲染|若是初始渲染条件为假 直到条件为真的前不进行渲染|不论初始条件为什么都进行渲染
`<temple>`元素支持|支持|不支持
