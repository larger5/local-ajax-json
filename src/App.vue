<template>
    <div id="app">
        <img src="./assets/logo.png">
        <div>
            <el-button @click="startHacking">Start</el-button>
            <el-table :data="heatChina" style="width: 100%">
                <el-table-column prop="name" label="名字"></el-table-column>
                <el-table-column prop="value" label="数值"></el-table-column>
            </el-table>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                heatChina: []
            }
        },
        created() {
            this.getAjaxData();
        },
        methods: {
            startHacking() {
                this.$notify({
                    title: 'It works!',
                    type: 'success',
                    message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
                    duration: 5000
                })
            },
            getAjaxData() {
                let that = this;
                axios.get('static/data/heatChinaRealData.json')
                    .then(function (response) {
                        console.log(response.data);
                        that.heatChina = response.data
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            }
        }
    }
</script>
<style>
    #app {
        font-family: Helvetica, sans-serif;
        text-align: center;
    }
</style>
