#### 基础语法
- 双向数据绑定
- 表单元素
    - `<input>`
    - `<textarea>`
    - `<select>`
- 语法糖
- **忽略** value checked selected 等特性初始值
- 输入的时候不会进行更新 要使用的话使用input事件

元素 |属性|事件
--|--|---
text textarea| `value`|`input`
checkbox radio|`checked`|`change`
select| `value`作为props|`change`

```html
//1. 文本
<input v-model="Message">
<p>{{Message}}</p>

//2. 多行文本
<p style="white-space:pre-line">{{message}}</p>
<textarea v-model="message"></textarea>

//3.1 单个复选框
<input type="checkbox" id="checkbox">
<label for="checkbox">{{ checked }}</label>

//3.2 多个复选框 绑定在同一个数组上


//4. 单选按钮
<input type="radio" id="one" value="One" v-model="picked">

//5.1 选择框单选
<select v-model="selected">
    <option disabled value="">请选择</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
</select>

//5.2 选择框多选 绑定到数组
<select v-model="selected" multiple>
    <option>A</option>
    <option>B</option>
    <option>C</option>
</select>
```

#### 值绑定
> 默认的值为 布尔值 或 子字符串 可以修改为自己指定的值

```html
//复选框
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no" 
>

// 单选按钮
<input type="radio" v-model="pick" v-bind:value="a">

// 选择框
<select v-model="selected">
    <!-- 内联对象字面量 -->
  <option v-bind:value="{ number: 123 }">123</option>
</select>
```

#### 修饰符

- `.lazy` 使用changge事件进行同步
- `.number` 自动将用户输入的值转化为数值
- `.trim` 过滤掉首尾空白符




