<template>
  <div class="content">
      <h1>我是真的帅啊</h1>
      <h2>你太菜了</h2>
      <!-- <img src="./666.jpg" alt="大唐不夜城"> -->
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'css01',
  components: {
      // HelloWorld
  },
  data() {
      return {}
  },
  mounted() { },
  computed: {},
  watch: {

  },
  methods: {}
}
</script>

<style lang="less" scoped>
h1 {
  color: red;
  font-size: 50px;
}
h2 {
  color: greenyellow;
  font-size: 70px;
}
</style>
