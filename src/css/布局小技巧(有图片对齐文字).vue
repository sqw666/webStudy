<template>
    <div class="content">
        <span>我很好</span>
        <span>我很好1</span>
        <div class="yy">
            <!-- <div class="yyy">
                内部盒子
            </div> -->
            <span class="yyyy">
                出来玩啊
            </span>
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
    overflow: hidden; //最好的解决塌陷的问题
    text-align: center;  // 可以让行内快和文本水平居中    
    line-height: 400px; // 可以让行内快和文本水平居中   
}
.yyy {
    width: 200px;
    height: 100px;
    margin: 0 auto;
    padding: 5px;
    border: 5px solid red;
    margin-top: 150px;   // 减去子盒子的高度除以二
    margin-top: 140px;  //要重新算
    text-align: center;
    line-height: 100px;  // 单行垂直  一般用于块元素和行内快
    // 布局和背景等不会继承，字体，颜色等会继承
    background-color: gray;
}
img {
    vertical-align: middle;  // 找的是旁边字的中心   字可能设计的问题 不一定在父盒子垂直中心线   字越小图片对的越齐  直接让父级fonsize 为0
}
span {
    vertical-align: middle;  // 找的是旁边字的中心   字可能设计的问题 不一定在父盒子垂直中心线   字越小span对的越齐  直接让父级fonsize 为0
}
.yyyy {
    background-color: orange;
    font-size: 20px;

}

.pp {
    width: 200px;
    height: 200px;
    background-color: khaki;
}</style>
