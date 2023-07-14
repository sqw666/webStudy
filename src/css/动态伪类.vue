<template>
    <div class="content">
        <a href="https://www.baidu.com"> 去百度</a>
        <a href="https://www.jd.com"> 去京东</a>
        <a href="https://www.jd.com"> 去京东</a>
        <input type="text">
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
// 没访问过
a:link {
    color: yellow;
}
// 访问过
a:visited {
    color: red;
}
// 悬浮  所有元素都有
a:hover {
    color: skyblue;
}
// 点中激活 所有元素都有
a:active {
    color: purple;
}
// 表单类的可以用focus

input:focus {
    color: red;
}

</style>
