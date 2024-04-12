# CSS兼容性多行省略

Vue 3 + TypeScript + Vite + less

使用css的float属性实现：

### 优点

1. 兼容性好，满足不是webkit内核的浏览器都能支持
2. 自适应宽度

### 缺点

1. 固定高度，不能自适应高度，因此显示多少行还要受字体大小限制
2. 需要为文字包裹一个标签用以设置样式
3. 从读样式代码上来看，理解起来不是很好理解

### 运行
`npm install`

`npm run dev`

### 使用
`MultipleLineOmission`组件支持传入两个参数：
```ts
interface MultipleLineOmissionProps {
   text: string,
   option?: {
      height: string,
      lineHeight: string,
      backgroundColor: string
   }
}
// 默认值：
const defaultOption: defaultOptionProps = {
   height: '100px',
   lineHeight: '25px',
   backgroundColor: '#fff'
}
```
`text`为传入的文本
#### 行数
值为`height / lineHeight`，默认为 `100 / 25 = 8` 行，可以在 `option` 自己定义

#### 背景颜色 backgroundColor
由于省略号是一个伪类，背景颜色默认是白色，如果父级组件的背景颜色不是白色的话需要在`option.backgroundColor`配置