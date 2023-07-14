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
// .box {
//     position: relative;
//     top: 0;
//     left: 0;
//     transition: 1s linear all;
// }
// .box:hover {
//     box-shadow: 0px 0px 20px black;
//     top: -1px;
//     left: 0;

// }
// 兼容性查询 caniuse.com
// 前缀是为了兼容测试期的浏览器，过了就不需要了，最后我们只写正常不加前缀直接写就完了，交给webpack。
// 长度单位，50vw是视口《宽度》的50%。20vh是视口高度的20%。 vmin vmax  。。。。。。。。。。。。。
// 电脑缩放125%，浏览器要改成80%才对。
// 怪异盒子，box-sizing
// resize + overflow  可以拉伸盒子大小
// 阴影box-shadow 水平位置 垂直位置 颜色/模糊程度 颜色   最常用的是这个四个值
// 水平值 垂直值 模糊程度 外沿值 阴影颜色 内阴影
// 10px   10px   80px   10px   red     inset  前提给背景色为黄色，就贼好看。  下面是小米效果
//     .box {
//     position: relative;
//     top: 0;
//     left: 0;
//     transition: 0.4s linear all;
// }
// .box:hover {
//     box-shadow: 0px 0px 20px black;
//     top: -1px;
//     left: 0;
// }
// opacity 不透明度，0是看不见，1是完全看见  它是一个属性能改变整个盒子，rgba一般是操作某个属性。
// background-origin 原点  默认值是padding-box   还有content-box
// background-clip 图片呈现区域  text 配合字体颜色是透明可以把图片搞在文字上666
// background-size cover等比例缩放 放弃了一部分
// border-radius 
// outline 外轮廓   但是不参与盒子大小计算  配合style color使用 还有一个offset
// 文本阴影text-shadow 但没有内阴影和外沿值，其余和盒子阴影一样。  0px 0px 15px black.
// 文本换行 white-space： pre/pre-wrap/pre-line / nowrap           
// 文本溢出c处理 先white-space：nowrap  再 text-overflow hidden + text-overflaw ellipsis 
// 文本修饰 text-decoration: overline dashed blue; 
// 文本描边 兼容性差 了解即可 text-stroke-color/width   一般配合文本颜色设置透明色。 
// 线性渐变background-image: linear-gradient(red, yellow, green);
// 线性渐变background-image: linear-gradient(to right, red, yellow, green);
// 线性渐变background-image: linear-gradient(to right top, red, yellow, green);
// 线性渐变background-image: linear-gradient(20deg, red, yellow, green);
// 线性渐变background-image: linear-gradient(red 50px, yellow 100px, green 150px);
// 线性渐变background-image: linear-gradient(50deg, red 50px, yellow 100px, green 150px);  把文字设置成透明色 在写-webkit-background-clip：text；
// 径像渐变 background-image: radial-gradient(red, yellow, green);
// 径像渐变 background-image: radial-gradient(at left top, red, yellow, green);
// 径像渐变 background-image: radial-gradient(at 100px 50px, red, yellow, green);
// 径像渐变 background-image: radial-gradient(circle, red, yellow, green);
// 径像渐变 background-image: radial-gradient(100px, 100px, red, yellow, green);
// 径像渐变 background-image: radial-gradient(red 50px, yellow 100px, green 150px);
// 径像渐变 background-image: radial-gradient(100px, 50px at 100px 120px ,red 50px, yellow 100px, green 150px);
// 重复渐变 background-image: repeating-linear-gradient(red, yellow, green);  有纯色未渐变的区域才会生效
// 重复渐变 background-image: repeating-radial-gradient(red, yellow, green);
// 渐变小案例 草稿纸
// web字体 定制字体  iconfont 阿里网站 生成后本地下载，全部复制过来，打开demo复制 @font-face里的配置，再改下路径就行。
// @font-face {
//     font-family: '自定义字体';
//     src: url('./666.jpg');  //引入字体 .ttf文件
// }
// 字体图标 阿里图标库
// 2D位移 transform: translateX(50px, 50px); 位移的百分比是自身   可以和定位配合实现垂直居中,  位移对行内元素无效 
// 2D缩放 transform: scale(1.5);  甚至也可以缩放字体 但只能缩放块元素
// 2D旋转 transform: rotateZ(-30deg);  rotateZ = rotete
// 2D扭曲 transform: skewX(-30deg);
// 2D多重变换 transform: translateX(50px, 50px) scale(1.5);  组合起来，  只有旋转会让坐标系跟着变，所有一般把旋转放后面。
// 2D多变换原点     transform-origin: left top;   变换原点队位移无影响，对缩放有影响
// 3D变换？
// 过渡属性 transition-property: width, hight;  // 设置哪个属性需要过渡效果  一般和hover用。  // all 让所有能过渡的东西都过渡
// 过渡时间 transition-duration: 1s, 2s; 
// 过渡延迟 transition-delay:2s; 
// 过渡线性速度匀速 transition-timing-function: linear;
// 过渡步长 transition-timing-function: steps(20); // 分成20份
// 跟数值过渡可以，不能跟none过渡， 过渡要写在原本样式上（谁想过渡），过渡后的效果（样子）要写在hover上。
// 贝塞尔曲线  可以出去又回来
// 符合顺序 transition： 时间 属性 延迟 速度；
// 过渡案例
// 动画的属性给想要动画的元素
// 动画名字     animation-name: wangyoudong;
// 动画时间     animation-duration: wangyoudong;
// 动画延迟     animation-delay
// 动画其他属性  调速度的  animation-timing-function: linear;
// 动画其他属性  调次数     animation-iteration-count: 3;  可以无限播放
// 动画其他属性  调方向         animation-direction: reverse;
// 动画其他属性  调方向         animation-direction: reverse;
// 动画其他属性  停在最后一帧       animation-fill-mode: forwards;
// 动画其他属性  播放状态         animation-play-state: paused; 暂停
// 动画复合属性 顺序就是上面的顺序 名字到播放状态，但是暂停一般放在hover里，否则直接就停了。
// 过渡要出发==触发条件事件，动画不需要，动画能更精细的定制，过渡只有始末。
// 一组关键帧
@keyframes wangyoudong{
    // // 第一帧
    // from {}
    // // 最后一针
    // to {
    // transform: translate(900px);

    // }
    // 0% {}
    // 29% {}
    // 100% {}

}   
// 多列布局     column-count: 3;  分三列 可以指定宽度  
// column-gap: 20px;  //  列间距
// 复合属性     column-rule: 2px dashed red; 边框
//     column-span: all;  横跨多列
// 图片多列布局， 父容器column-count: 3;  img标签 width：100%；
// 弹性盒子  不用清除浮动，可以撑开父元素，没漂。
// display: flex;
// display: inline-flex;不仅变为伸缩容器还变成了行内快，会出现缝隙（空格）
// 只要加了flex  本身元素和子元素全干成块，无论行不行内。  可以在控制台computed show all。
// 主轴方向     flex-direction: row/row-reverse/column; 只要动了，侧轴也会跟着相对动，因为侧轴手动改不了。
// 主轴换行方式 flex: wrap;  // 否则子元素会收缩宽度     还有no-wrap/wrap-reverse；
// 复合属性 flex-flow: row wrap; 没必要写 会乱
// 主轴对齐方式    justify-content: flex-start、end / space-around/ center /space-between、evenly;
// 侧轴对齐方式   align-items: flex-end;  / center  主轴会过日子，侧轴不会 
// 侧轴对齐方式（多行） 多行是指主轴上多行，注定和align-items互斥      align-content: flex-start;/space-around/ center /space-between / evenly  默认是不会过日子。 
// 水平居中 第一种 给父亲display flex，子元素margin：auto; 
        // 第二种给父亲 justify-content align-items center 
// 基准长度     flex-basis: 300px;  会顶掉原来的在主轴上的基准长度，看主轴方向。
// 伸 加flex-grow: 2; 瓜分剩余空间
// 父亲空间不够了，会产生压缩。把换行属性去掉，就会压缩
// 父亲空间不够了，  压缩比flex-shrink: 1; 默认为1
// 复合属性 flex:1; 可以拉伸 可以压缩 基准长度为0； 
// 可以单独排序 order：-1； 跑前面了
// 可以单独某行的侧轴位置     align-self: center; 
// 案例  html，body都设置100%高宽
// 给父亲 height：calc(100vh-70px);  子元素margin： 0 auto；  可以垂直居中  这个案例做网站首页 sqw sqw代表重要有用
// 响应式布局 媒体查询
// 媒体类型 
// 只有在打印机或打印预览才会应用的样式。  先写正常的样式，媒体查询的样式写在下面，不然会被顶掉。
// @media print {
// background: red;
// }
// @media screen/ all / not screen / only screen{ 
    
// }

//(width: 800px)视口高度在800px生效
//视口宽度在800px生效
// @media (width: 800px) { 
    // h1 {
    //     background-color: green;
    // }
    
// }

// @media (max-width: 800px) {   小于等于
    // h1 {
    //     background-color: green;
    // }
    
// }
// @media (min-width: 800px) {   大于等于
    // h1 {
    //     background-color: green;
    // }
// }
// device-width: 800px   设备宽度
// @media screen and (min-width: 800px) and (maxin-width: 900px) {   是屏幕且800-900生效
// @media screen and (max-width: 800px) , (min-width: 900px) {   小于800或者大于900  ,和or 都是或的意思
 
    // h1 {
    //     background-color: green;
    // }
    
// }
// 常用阀值 768 992 1200    超小屏幕 中等 大  超大
// 每一个区间都要写一套样式 响应式布局...........
// BFC 元素的特异功能，满足某些条件后激活该功能。
// BFC 特点 1解决塌陷 2不会被其他元素压住 3子元素浮动 也不会让父元素高度塌陷。
.box {
    // animation-name: wangyoudong;
    // animation-iteration-count: 3;
    // animation-direction: reverse;
    // animation-fill-mode: forwards;
    // animation-play-state: paused;
    // column-count: 3;
    column-gap: 20px;
    column-rule: 2px dashed red;
    column-span: all;
    justify-content: space-around;




    
    



}

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
