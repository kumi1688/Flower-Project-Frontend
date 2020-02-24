<template>
    <v-container v-if="this.dataList.length !== 0">
        <ul>
            <v-list-item v-for="data in dataList" v-bind:key="data._id">
                <v-list-item-content style="width: 20%">
                    <v-list-item-title>온도</v-list-item-title>
                </v-list-item-content>
                <v-list-item-action style="width: 90%">
                    <v-progress-circular
                            width="10"
                            size="60"
                            :value=data.sensorData.temperature>{{data.sensorData.temperature}}</v-progress-circular>
                </v-list-item-action>
            </v-list-item>
        </ul>
    </v-container>
</template>

<script>
import axios from 'axios';

    export default {
        name: "SensorContainer",
        created() {
            axios.get('/api/sensor').then((result) =>{
                const newData = {
                    sensorData: result.data.sensorData,
                    date: result.data.date,
                    device: result.data.device,
                    _id: result.data._id
                };
                this.dataList = this.dataList.concat(newData);
                console.log(this.dataList[0].sensorData.temperature);
            });
        },
        data(){
            return{
                dataList: [],
            }
        },
        methods:{

        }
    }
</script>

<style scoped>

</style>
