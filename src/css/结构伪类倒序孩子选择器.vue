<template>
    <div class="content">
       <span>1</span>
       <p>2</p>
       <p>2</p>
       <p>2</p>
       <p>2</p>
       <p>2</p>
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
//倒序
div>p:nth-last-child(3) {
    color: red;
}
div>p:nth-last-of-type(4) {
    color: gold;
}
//这个span是父亲唯一的span和唯一孩子
span:only-child {
    color: aqua;
}
// 这个是不能出现同类型span兄弟的的选择器
span:only-of-type {
    color: hotpink;

}
//根元素
/deep/ :root {
    background-color: hotpink;
}
//选中的是div且里面不能有内容
div:empty {
    width: 200px;
    height: 200px;
    background-color: hotpink;
}

</style>
