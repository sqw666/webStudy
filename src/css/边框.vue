<template>
    <div class="content">
        <span>9999999999999999999999</span>
        <!-- <table border="1"> -->
        <table>
            <caption>人员信息</caption>
                <tr>
                    <th>序号</th>
                    <th>姓名</th>
                    <th>年龄</th>
                    <th>面貌</th>
                </tr>
                <tr>
                    <td>1</td>
                    <td>张三</td>
                    <td>17</td>
                    <td>群众</td>
                </tr>
                <tr>
                    <td>1</td>
                    <td>张三</td>
                    <td>17</td>
                    <td>群众</td>
                </tr><tr>
                    <td>1</td>
                    <td>张三</td>
                    <td>17</td>
                    <td>群众</td>
                </tr><tr>
                    <td>1</td>
                    <td>张三</td>
                    <td>17</td>
                    <td>群众</td>
                </tr>
        </table>
        
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
table {
    // border-width: 2px;
    // border-color: green;
    // border-style: solid;
    border: 2px greenyellow solid;
}
td,th {
    border: 2px red solid;

}
span {
    border: 2px greenyellow solid;

}
</style>
