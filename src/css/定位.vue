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
// position relative 相对定位，给本身left值后会相对于他原来位置向左移动值
// 相对定位的层级要高，可以盖住其他普通盒子，且占原来位置。 都开相对定位时，后写的可以盖住先写的
// 相对定位可以与margin一起用，但不推荐. 也可以与浮动一起用，都起了作用，先浮动再位移。都不推荐定位和他俩一起用。
// 子绝父相  往上找相对，相对那个开启定位（啥定位都行）的盒子，找不到就相对于body.
// 绝对定位开启后，像浮动一样，标准流会上去被压，但不会把下面的标准流文字踢出来。
// 绝对定位的盒子比较狠，它是定位元素可以直接设置宽高，无论是不是块。相对定位的盒子就不行。定位元素的宽高是默认撑开的。
// 绝对定位还经常与hover配合，hover后，给他left值。       需要祖先级元素有相对定位.
// 固定定位给left值，但他只找视口再位移。加上fix后也是定位元素了。
// 粘性定位，滚d动会停住，阅读完就又走了。必须要祖先某个盒子真实可滑动。
// 粘性定位 position:sticky   top : 10px (离他最近的能滚动的祖先元素 当胶水的父容器的内容走完了，胶水就失效了)
// 粘性定位也不推荐和浮动和margin一起用 .
// 无论什么定位,层级是一样的,看dom谁后加载谁大.
// 一般只有定位才可以加z-index，一般大的会被它的包容块拖累，不一定越大就一定越大。
// 定位可以越过padding（无视祖先的padding）
// 父亲相对不给宽度，子绝对，给百分比宽度100，如果再给子padding和border，会超出父亲范围，解决办法，不给子100百分比宽度，给子left 0  right 0；当然都给一点会居中，再给子top 0 bottom 0 ，会让子的边框成为父亲的内边框，相当于给父亲padding上色。？。
// 垂直居中，margin 0 auto，垂直的要算再用margin-top，但要给父亲overflow hidden。
// 第二种，子绝父相之后，给子left right top bottom 0 ,再加一句margin 0 auto。
// 第二种的第二小种，跟margin有关，算了 不推荐。 

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
