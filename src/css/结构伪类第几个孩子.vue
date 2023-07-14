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
// 最后一个p元素且是最后一个孩子
div>p:last-child {
    color: seagreen;

}
// span 后面的第二个div且该div必须为第二个孩子
span div:nth-child(2) {
    color: fuchsia;
}
// n初始为0
span div:nth-child(2n + 1) {
    color: fuchsia;
}
// 前五个且是div
span div:nth-child(-n + 5) {
    color: blue;
}
// span后面第一个div类型
span div:first-of-type {
    color: gold;
}
span div:last-of-type {
    color: darkmagenta;
}
// span后面只看div类型中的第二个
span div:nth-of-type(2) {
    color: tomato;
}
</style>
