<template>
    <div class="content">
        <button @click="buttonClick">点击触发事件</button>
    </div>
</template>

<script>
// let有块作用域 {} 。 作用域还有 全局 函数 eval(es5严格模式)
// let不存在变量提升，而var会提升 并且赋值undefined。
// 不影响作用域链的变量查找规则。
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
export default {
    name: "css01",
    components: {
        // HelloWorld
    },
    data() {
        return {};
    },
    mounted() {},
    computed: {},
    watch: {},
    methods: {
        buttonClick() {
            alert('不要点我啦')
            console.log('你好JS')
        }
    },
};
</script>

<style lang="less" scoped>

</style>
