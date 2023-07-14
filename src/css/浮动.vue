<template>
    <div class="content">
        <span>我很好</span>
        <span>我很好1</span>
        <div class="yy">
            <img src="./666.jpg" alt="">
        </div>
        
        <div class="pp"></div>
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
.yy {
    width: 400px;
    height: 400px;
    background-color: green;
    // float: left;  //  最早是为了可以实现图片 文字环绕
    // 浮动后的元素   d大小宽高由它内容撑开，旁边的盒子文字也还保留着文字环绕效果
    // 特点 不会独占一行 也没有塌陷问题，不会像行内快一样当文本处理，比如text-alian 居中不生效了
}
img {
    width: 400px;
}
.pp {
    width: 200px;
    height: 200px;
    background-color: khaki;   
}
</style>
