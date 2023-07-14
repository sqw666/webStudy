<template>
    <div class="content">
        <div class="ddd">111</div>
        <div class="fff">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Consequuntur molestiae praesentium assumenda totam, provident quas nobis possimus eaque incidunt tempore magnam consectetur natus beatae omnis mollitia suscipit. Necessitatibus, excepturi accusantium.</div>
        <span>我很好</span>
        <div class="tt">hiflksdfhjklsdghjfkdfhg</div>
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
    display: block;
    // display: none;
    // width: 600px; // 写死宽度会出滚动条  不给就是撑开 继承父容器 一般不与width同时用
    // min-width: 500px;
    max-width: 1000px;  // 暗中给你最小值
    // height: 200px;
    // max-height: 400px;
    min-height: 50px;
    // padding: 20px;
    // padding-left: 20px;
    padding: 20px 0 0 0;  //上开始顺序
    margin: 50px;
    font-size: 20px;
    border: 2px transparent solid;
    background-color: rgb(255, 179, 0);
    cursor: pointer;
}
span {
    background-color: orange;
    font-size: 20px;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
    padding-bottom: 20px;  // 行内元素上下的padding不占位置 不能完美设置 会飘起来   块不会
}
.tt {
    width: 300px;
    height: 300px;
    background-color: skyblue;
    border-width: 10px;
    // border-left-width: 50px;
    border-color: aqua;
    border-top-color: gold;
    border-style: solid;
    border-bottom-style: dotted;
    // border-left: 20px solid purple;
    // border: 10px solid red;
}
</style>
