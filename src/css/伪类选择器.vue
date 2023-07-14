<template>
    <div class="content">
        <a href="https://www.baidu.com"> 去百度</a>
        <a href="https://www.jd.com"> 去京东</a>
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
a:link {
    color: yellow;
}
a:visited {
    color: red;
}

</style>
