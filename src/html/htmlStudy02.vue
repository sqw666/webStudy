<template>
  <div class="content">
       <marquee loop="1">666</marquee>
       行内元素不要写块级元素，不好调样式，浏览器会错乱
       h标签不能相互嵌套
       p标签中不能写块级元素
       <!-- <img width="100px" src="./001.jpg" alt="奥特曼"> -->
       ./是当前位置
       ../跳出来上一级
       alt是图片描述，也能让浏览器知道这个图片的内容
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'htmlStudy01',
  components: {
    // HelloWorld
  }
}
</script>
