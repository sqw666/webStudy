<template>
    <div class="content">
        <span>我很好</span>
        <span>我很好1</span>
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
.yy {
    width: 200px;
    height: 200px;
    background-color: green;
    visibility: hidden; // 隐藏了  但是占位
    display: none; // 隐藏 但不占位
}

.pp {
    width: 200px;
    height: 200px;
    background-color: khaki;
}</style>
