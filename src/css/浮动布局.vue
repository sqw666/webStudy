<template>
    <div class="content">
        <div class="yy">
            <div class="box box1"></div> 
            <div class="box box2"></div> 
            <div class="box box3"></div> 
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
// 浮动产生的问题    父亲的高度塌陷没了  和 后面的标准流抢占位置，且内容环绕浮动的盒子
// 第一种 给父亲高 ，但是子元素后面的标准量盒子抢占位置，且内容环绕浮动的盒子
// 第二种 给父亲浮动， 都不占位置，父亲后面的标准量盒子抢占位置，且内容环绕浮动的盒子
// 第三种 overflow hidden  还是后面的兄弟标准量盒子抢占位置 文字也切了
// 第四种  clear both 给兄弟后面的标准量盒子加上， 清楚前面所有浮动兄弟的影响  前提是它本身没有浮动且不能是行内元素
// 第四种需要在浮动兄弟后面额外写个盒子给它clear both 之后宽高啥都不给，就解决了
// 第五种 直接在父亲后面加伪类 本质就是第四种   d但是有个缺陷，万一最后有个标准子兄弟，他有没有clear属性，就炸了，所以有个原则一个父元素里面要么一起浮动，要么一起不飘
// 总结 父元素里要浮动就要全浮动，再给父亲加个伪类
// .yy::after {
//     content: '';
//     display: block;
//     clear: both;
// }

// 浮动布局 子元素浮动后给父元素加清除浮动，且子元素要么全浮动，要么都不浮动。还有一个注意点用margin隔开其他盒子，padding会撑大盒子，除非给border-size = box-size
.yy {
    background-color: gray;
}
// .yy::after {
//     content: '';
//     display: block;
// }
.box {
    background-color: orange;
    height: 100px;
    width: 100px;
    float: left;
}
.box2 {
    background-color: red;
}
.box3 {
    background-color: rgb(0, 255, 51);
}
.box4 {

}
</style>
