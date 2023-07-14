<template>
    <div class="content">
        <p>999</p>
        <p>899</p>
        <p>99</p>
        <input type="text" placeholder="666">
       Lorem ipsum dolor, sit amet consectetur adipisicing elit. Cupiditate, fuga dolorum quibusdam qui sequi non distinctio officiis accusamus labore blanditiis, sint porro? Illum odio voluptatibus numquam repellat dignissimos ratione cumque!
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
// 选中div中的第一个文字
div::first-letter {
    color: red;
    font-size: 66px;
}
// 选中div中的第一行文字
div::first-line {
    color: rebeccapurple;
    font-size: 24px;
}
// 选中的是div中被鼠标选择的文字
div::selection {
    background-color: green;
    color: orange;
}
// 选中的是input中提示的文字
input::placeholder {
    color: skyblue;
}
//内容开始前面创建一个子元素
p::before {
    content: "￥";
}
p::after {
    content: ".00";
}

</style>
