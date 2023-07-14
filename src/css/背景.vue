<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <div class="ddd">
            sdddddgfdlglfdkgl
        </div>
        
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

span {
    border: 2px greenyellow solid;

}
.ddd {
    color: fuchsia;
    width: 400px;
    height: 400px;
    border: 2px lawngreen solid;
    // background-color: hotpink;
    background-image: url('./666.jpg');
    // background-repeat: repeat-x;
    background-repeat: no-repeat; // 平铺方式
    // background-position: right top;  // 背景图片位置
    // background-position: center center;  // 背景图片位置
    background-position: 20px 20px;  // 背景图片位置  图片所在的坐标系
    background: skyblue url('./666.jpg') no-repeat 20px;
    

}
</style>
