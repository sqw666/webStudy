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
    line-height: 400px; // 可以让行内快和文本垂直居中   
}
.yyy {
    width: 200px;
    height: 100px;
    margin: 0 auto;
    padding: 5px;
    border: 5px solid red;
    margin-top: 150px;
    margin-top: 140px;  //要重新算
    text-align: center;
    line-height: 100px;  // 单行垂直  一般用于块元素和行内快

    // 布局和背景等不会继承，字体，颜色等会继承
    background-color: gray;
}
img {
    // vertical-align: top;
    vertical-align: bottom;   // 解决方案   控制了字的位置   推荐这种
    // 行内快于与块元素下面会有空白是幽灵空白，因为与底下的字基线对齐了他默认baseline，所有留有空白,
    display: block;   // 第二种  变成块也可以解决幽灵空白，他会变成块独占一行，但不能后面有字。
    font-size: 0;    // 第三种
}
.yyyy {
    background-color: orange;
    font-size: 20px;                          // 解决元素之间的空白问题，不留空格就可以，但不推荐，推荐是给父元素字体大小为0，因为空格也属于字体，再单独给子元素设置字体

}

.pp {
    width: 200px;
    height: 200px;
    background-color: khaki;   
}</style>
