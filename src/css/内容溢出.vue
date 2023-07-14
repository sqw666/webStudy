<template>
    <div class="content">
        <span>我很好</span>
        <span>我很好1</span>
        <div class="tt">
            <div class="inner"></div>
        </div>
        <div class="yy"></div>
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
span {
    background-color: orange;
    font-size: 20px;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
    padding-bottom: 20px; // 行内元素上下的padding不占位置 不能完美设置 会飘起来   块不会   t图片之间有回车会有缝隙
}

span {
    margin-right: 20px;
    margin-top: 400px; //不生效 行内元素不能设置上下的margin  padding的也不完美不占位，块才可以
    margin: 0 auto; // 居中不可以 块才可以

}

.tt {
    width: 400px;
    height: 400px;
    padding: 50px;
    background-color: skyblue;
    border: 10px solid red;
    margin-left: auto; //离左边能有多远就有多远
    margin: 0 auto; // 居中 在父元素之内水平居中

}

.inner {
    width: 100px;
    height: 100px;
    margin: 100px; // 子元素的margin是基于父元素的内容区的 不包括父元素的padding
    background-color: orange;
}

.yy {
    width: 200px;
    height: 200px;
    // margin-top: 20px;
    // margin-bottom: 50px;
    background-color: green;
}

.pp {
    width: 200px;
    height: 200px;
    // margin-top: 20px;
    margin-top: -60px; // 压住上面了  
    margin-bottom: 60px; // 最后一个子元素的margin-bottom和第一个子元素的margin-top会被父容器抢走，历史遗留问题。三个解决方案，1给父容器加border,2给父容器加padding3最好的的是overflow hidden
    // overflow: hidden;
    // margin-top: 60px;  // 上下两个盒子的margin合并，上盒子的margin-bottom和下盒子的margin-top会取最大值保留。

    background-color: khaki;
    // overflow: hidden;  auto 和hidden 是常用的值  还有一个scroll 默认是visible
    // overflow-x: hidden; // 实验中的属性
    // overflow-y: visible;  x y不能一个hidden一个visible 实验中的属性
}</style>
