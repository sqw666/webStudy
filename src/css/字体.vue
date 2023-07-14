<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <p class="p1">88888888888生物地理水利电力</p>
        <p class="p2">88888888888生物地理水利电力</p>
        <p class="p3">88888888888生物地理水利电力</p>
        <p class="p4">生物地理水利电力</p>
       Lorem ipsum dolor, sit amet consectetur adipisicing elit. Cupiditate, fuga dolorum quibusdam qui sequi non distinctio officiis accusamus labore blanditiis, sint porro? Illum odio voluptatibus numquam repellat dignissimos ratione cumque!
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
div {
    font-size: 20px;
    font-family: '微软雅黑';
}
.p2 {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;

}
.p3 {
    // sans-serif  随机找个非衬线
    // 找到为止
    font-family: 'STHupo', '宋体', '楷体', '华文彩云' , sans-serif;
}
div .p4 {
    font-family: 'STHupo';
    // 斜体
    font-style: italic;
    font-weight: 900;
    // 要顺序 最后两位 是大小和簇
    font: 100px "华文彩云";
}
span {
    //最小就是12px
    font-size: 3px;
}
</style>
