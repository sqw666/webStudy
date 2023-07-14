<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <ul>
            <li>666666666</li>
            <li>5555555555</li>
            <li>666666666</li>
            <li>666666666</li>
        </ul>
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
ul {
    // list-style-type: none;
    // list-style-type: upper-alpha;
    list-style-type: decimal;
    list-style-position: outside; // 让序号在列表内容外面
    list-style-image: url('./666.jpg'); // 自定义列表符号
    // list-style: decimal inside url('./666.jpg'); // 可以一起写

}
li {
    background-color:orange;

}
</style>
