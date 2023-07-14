<template>
    <div class="content">
       <span>1</span>
       <p>2</p>
       <p>2</p>
       <p>2</p>
       <p title="你要加油啊">888</p>
       <p class="eee">2</p>
       <div></div>
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
div>p:not(.eee) {
    color: red;
}
div>p:not([title^="你要加油"]) {
    color: yellow;
}
// 选中div后面的p元素，但是排除第一个p
div>p:not(:first-child) {
    color: blue;
}
</style>
