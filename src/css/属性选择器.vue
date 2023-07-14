<template>
    <div class="content">
        <h1>我是真的帅啊
            <i>66666666666</i>
        </h1>
        <h2 title="rr">你太菜了77</h2>
        <h2 title="rrrr">你太菜了70</h2>
        <p>我在哪</p>
        <p>我在哪1</p>
        <i class="ppp">你太菜了</i>
        <i class="ppp">你太菜了1</i>
        <!-- <p id="earthy">万水千山总是情，爱我多点行不行</p> -->
        <!-- <p class="answer">曾经沧海难  为水，除却巫山不是云</p> -->
        <!-- <img src="./666.jpg" alt="大唐不夜城"> -->

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

// .answer {
//     color: skyblue;
// }
// #earthy {
//     color: hotpink;
// }
div p {
    color: darkgoldenrod;
}
div i.ppp {
    // color: aqua
};
div>i {
    color: aquamarine;
}
//选中div后紧紧相连的兄弟p元素
h2+p {
    color: peru;
}
// p后面所有的i兄弟元素
p~i {
    color: red;
}
[title] {
    color: purple;
}
//可以写正则
[title^='rrrr'] {
    color: rosybrown;
}
</style>
