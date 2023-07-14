<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <div class="ddd">
            sdddddgfdlglfdkgl
            <input type="text">
        </div>
        
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

span {
    border: 2px greenyellow solid;

}
.ddd {
    color: fuchsia;
    width: 400px;
    height: 400px;
    border: 2px lawngreen solid;
    cursor: pointer;
    
}
input {
    cursor: url('./777.png'), pointer;
    }
</style>
