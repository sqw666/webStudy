<template>
    <div class="content">
        <span>我很好</span>
        <span>我很好1</span>
        <div class="yy">
            <div class="yyy">
                内部盒子
            </div>
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
    width: 200px;
    height: 200px;
    padding: 20px;
    font-size: 40px;
    font-weight: bold;
    color: red;
    background-color: green;
    // visibility: hidden; // 隐藏了  但是占位
    // display: none; // 隐藏 但不占位
    // 控制台的样式展示顺序
    // 行内样式
    // 内部样式
    // 默认样式  是agent代理  可以顶掉继承的样式，继承的最低
    // 继承样式   
    // 可能中间会穿插一个外联样式 index.css?_6733438
    
}
.yyy {
    height: 200px;
    // 布局和背景等不会继承，字体，颜色等会继承
    background-color: gray;
}

.pp {
    width: 200px;
    height: 200px;
    background-color: khaki;
}</style>
