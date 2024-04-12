<script setup lang="ts">
import MultipleLineOmission from '@/components/multiple-line-omission'
const text1 = '无可否认，当读者在浏览一个页面的排版时，难免会被可阅读的内容所分散注意力。Lorem Ipsum的目的就是为了保持字母多多少少标准及平均的分配，而不是“此处有文本，此处有文本”，从而让内容更像可读的英语。如今，很多桌面排版软件以及网页编辑用Lorem Ipsum作为默认的示范文本，搜一搜“Lorem Ipsum”就能找到这些网站的雏形。这些年来Lorem Ipsum演变出了各式各样的版本，有些出于偶然，有些则是故意的（刻意的幽默之类的）。'
const text2 = '恰恰与流行观念相反，Lorem Ipsum并不是简简单单的随机文本。它追溯于一篇公元前45年的经典拉丁著作，从而使它有着两千多年的岁数。弗吉尼亚州Hampden-Sydney大学拉丁系教授Richard McClintock曾在Lorem Ipsum段落中注意到一个涵义十分隐晦的拉丁词语，“consectetur”，通过这个单词详细查阅跟其有关的经典文学著作原文，McClintock教授发掘了这个不容置疑的出处。Lorem Ipsum始于西塞罗(Cicero)在公元前45年作的“de Finibus Bonorum et Malorum”（善恶之尽）里1.10.32 和1.10.33章节。这本书是一本关于道德理论的论述，曾在文艺复兴时期非常流行。Lorem Ipsum的第一行”Lorem ipsum dolor sit amet..”节选于1.10.32章节。'
const option1 = {
  height: '75px',
  backgroundColor: '#eee'
}
const option2 = {
  height: '200px',
  backgroundColor: '#f1d7d7'
}
</script>

<template>
  <div>
    <h3>三行省略：</h3>
    <div class="father-wrap" :style="{backgroundColor: '#eee'}">
      <MultipleLineOmission :text="text1" :option="option1"></MultipleLineOmission>
    </div>
  </div>
  <div>
    <h3>八行省略：</h3>
    <div class="father-wrap" :style="{backgroundColor: '#f1d7d7'}">
      <MultipleLineOmission :text="text2" :option="option2"></MultipleLineOmission>
    </div>
  </div>
</template>

<style>
.father-wrap {
  width: 600px;
}
</style>
