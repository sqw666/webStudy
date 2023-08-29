<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <!-- <div class="ddd">
            sdddddgfdlglfdkgl
            <input type="text">
        </div> -->
        <div class="eee">
            sdddddgfdlglfdkgl
            <input type="text">
        </div>
        <div class="fff">
            66633333
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
    cursor: pointer;
    
}
.eee {
    color: fuchsia;
    font-size: 20px;
    width: 30em;    // 等于字体大小20 * 30  等同乘以继承的字体大小 一层一层找
    height: 30em;
    border: 2px rgb(34, 0, 252) solid;
    cursor: pointer;
}
.fff {
    width: 20rem;   // rem是相对于html元素的字体大小的倍数
    height: 40rem;
    border: 2rem rgb(252, 0, 214) solid;
    font-size: 150%; // 相对于父元素的字体大小
    // width: 20%; // 相对于父元素
    // height: 20%;
    text-indent: 2em;  // 缩进

}

</style>
