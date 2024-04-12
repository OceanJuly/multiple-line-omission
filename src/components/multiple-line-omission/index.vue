<script setup lang="ts">
import {defaultOptionProps} from "./interface.ts";
import {onMounted, reactive} from "vue";

const props = defineProps<{
  text: string
  option?: Partial<defaultOptionProps>
}>()
const defaultOption: defaultOptionProps = {
  height: '100px',
  lineHeight: '25px',
  backgroundColor: '#fff'
}
let opt = reactive<defaultOptionProps>(defaultOption)
onMounted(() => {
  handleStyle()
})
function handleStyle() {
  Object.assign(opt, props.option || {})
}
</script>

<template>
  <div class="wrap" :style="{'--bg': opt.backgroundColor || '#eee', '--lineHeight': opt.lineHeight, '--height': opt.height}">
    <span class="content">
      {{ text }}
    </span>
  </div>
</template>

<style lang="less">
.wrap {
  /* 需要定高 */
  height: var(--height);
  /* 用来设置显示多少行才省略，值一般为wrap的height值/行数求得，但是这个行数会受到字体大小的限制 */
  /* 字体太大了，设置显示很多行也会很丑，都挤一块了，所以这个实际值，要看具体需求和实践 */
  line-height: var(--lineHeight);
  /* 加上此属性显示效果更佳，就算部分浏览器不支持也影响不大 */
  text-align: justify;
  overflow: hidden;
}

.wrap:before {
  float: left;
  /* 这个值可以随意设定，不论单位还是什么 */
  width: 1em;
  height: 100%;
  content: '';
}

.wrap:after {
  float: right;
  /* 大小随意，设置em单位最好，可随字体大小变化而自适应 */
  /* 如果要采用以下渐变效果，那么这个值要大于before里的width值效果会比较好点 */
  /* 值越大，渐变的效果越明显影响的范围越大。 */
  width: 2.5em;
  /* 与父元素wrap的行高实际px值一样 */
  height: 25px;
  /* 此值要跟自身宽度一样，取负值 */
  margin-left: -2.5em;
  /* 此值要跟before宽度一样 */
  padding-right: 1em;
  content: '...';
  text-align: right;
  /* 这里开始利用在float布局的基础上进行定位移动了 */
  position: relative;
  /* 与父元素wrap的行高实际值一样，取负值 */
  top: -25px;
  left: 100%;
  /* 设置渐变效果是为了省略号和内容衔接得自然点，没那么突兀，要注意要跟文字所在的背景的颜色搭配（把white替换成背景色） */
  background: #fff;
  background: linear-gradient(to right, rgba(255, 255, 255, 0), var(--bg) 50%, var(--bg));
}

.wrap .content {
  float: right;
  /* 该值要等于wrap:before的width值 */
  margin-left: -1em;
  width: 100%;
}
</style>