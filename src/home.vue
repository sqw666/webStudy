<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <html-study-01 />
  </div>
</template>

<script>
// @ is an alias to /src
import htmlStudy01 from '@/test/test.vue'

export default {
  name: 'HomeView',
  components: {
    htmlStudy01
  }
}
</script>
