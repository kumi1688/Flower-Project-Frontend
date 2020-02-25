<template>
    <v-container>
        <sensor-component v-bind:dataList="dataList" v-bind:totalDeviceNumber="totalDeviceNumber"></sensor-component>
        <h3>{{this.test}}</h3>
        <h2>{{this.count}}</h2>
        <button @click="increment">증가</button>
    </v-container>
</template>

<script>
import axios from 'axios';
import SensorComponent from "../component/SensorComponent";
import io from 'socket.io-client';
var socket = io('http://localhost:3000');

    export default {
        name: "Sensor",
        components:{
            'sensor-component' : SensorComponent
        },
        data(){
            return{
                websocketData: [],
                dataList: [],
                totalDeviceNumber: 0,
                count: 0,
                test: 'test'
            }
        },
        created() {
            axios.get('/api/sensor').then((result) => {
                this.dataList = result.data.deviceDataList;
                this.totalDeviceNumber = result.data.totalDeviceNumber;
            });
            this.getRealTimeData();
        },
        updated() {
            console.log('updated');
        },
        mounted() {
            // this.getData();
        },
        computed:{
          webSocketData2(){
              return this.websocketData
          }
        },
        methods:{
            connect(){
                socket.on('connect', function(){
                    console.log('웹 소켓 연결됨');
                });


                // socket.on('disconnect', function(){});
            },
            increment(){
                this.count = this.count + 1;
                // this.websocketData = this.websocketData.concat('345');
            },
            getRealTimeData(){
                socket.on("realTimeData", fetchedData => {
                    this.test = fetchedData.message;
                    this.dataList = fetchedData.data.deviceDataList;
                    this.totalDeviceNumber= fetchedData.data.totalDeviceNumber;
                    console.log(this.dataList);
                })
            }
        }
        }

</script>


<style scoped>


</style>
