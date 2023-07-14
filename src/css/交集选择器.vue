<template>
    <div class="content">
        <h1 class="rich">我是真的帅啊</h1>
        <h2 class="beauty">你太菜了</h2>
        <p class="beauty">我在哪</p>
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
.rich {
    color: gold;
}
.beauty {
    color: red;
}
p.beauty {
    color: purple;
}
</style>
