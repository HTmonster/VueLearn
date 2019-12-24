#### 监听事件
```
//v-on 监听DOM事件 触发JS代码
<div id="example">
    <button v-on:click="counter+=1">Add 1</button>
    <p>{{counter}}</p>
</div>
```
```
var vm=new Vue({
    el:'#example',
    data:{
        counter:0
    }
})
```
#### 事件处理方法
```

<button v-on:click="counter+=1"></button>//1. 简单表达式
<button v-on:click="func1"></button>//2. 绑定方法
<button v-on:click="func2('para')"></button>//3. 绑定内联方法
```
```
//v-on 可以接受一个调用的方法

methods:{
    func1:function(){
        xxxxx
    },
    func2:function(para){
        xxxxx
    }
}
```

#### 事件修饰符
```
<a v-on:click.stop="doThis"></a> //阻止单击事件继续传播 
<a v-on:submit.prevent="onSubmit"></a> //对于触发的事件调用 event.preventDefualt()
<a v-on:click.capture="doThis"></a> //内部触发的元素先在这里处理 再交给内部元素
<a v-on:click.self="doThis"></a> //当event.target时元素本身的时候触发
<a v-on:click.once="doOnce"></a> //事件触发一次
<a v-on:click.passive="doThis"> //修饰符表示就是设置{passive:true}，表示处理事件函数中不会调用preventDefault函数
```
#### 按键修饰符
```
v-on:keyup.enter
v-on:keyup.tab
v-on:keyup.delete //删除和退格
v-on:keyup.esc
v-on:keyup.space
v-on:keyup.up
v-on:keyup.down
v-on:keyup.left
v-on:keyup.right
```

#### 系统修饰符
```
.ctrl
.alt
.shift
.meta  //window 和 command
.exact

<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button @click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button @click.exact="onClick">A</button>

.left
.right
.middle
```

