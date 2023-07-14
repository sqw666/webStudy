<template>
    <div class="content">
        <p>11</p>
        <p>11</p>
        <p>11</p>
        <p>11</p>
        <p>11</p>
        <span>
            <i>333</i>
            <div>11</div>
            <div>11</div>
            <div>11</div>
            
        </span>
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
// div后面的第一个元素且是p元素
div>p:first-child {
    color: red;
}
// i必须是span后面某个同等级的第一个元素
span i:first-child {
    color: orange;
}
// 是p且是某个父亲的第一个孩子
p:first-child {
    color: aqua;
}

</style>
