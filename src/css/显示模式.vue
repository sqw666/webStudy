<template>
    <div class="content">
        <div class="ddd">111</div>
        <div class="fff">111</div>
        <div>111</div>
        <div>111</div>
       
    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
    name: "css01", 
    components: {
        // HelloWorld
    },
    data() {
        return {};
    },
    mounted() { },
    computed: {},
    watch: {},
    methods: {}, 
};
</script>

<style lang="less" scoped>
.fff {
    // color: fuchsia;
    // width: 600px;   不给就是撑开
    height: 200px;
    border: 2px rgb(231, 252, 0) solid;
    background-color: rgb(255, 179, 0);
    cursor: pointer;
    // display: block;
    display: none;
}
</style>
