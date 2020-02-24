<template>
    <v-container>
        <sensor-component v-bind:dataList="dataList" v-bind:totalDeviceList="totalDeviceNumber"></sensor-component>
    </v-container>
</template>

<script>
import axios from 'axios';
import SensorComponent from "../component/SensorComponent";
import io from 'socket.io-client';

    export default {
        name: "Sensor",
        components:{
            'sensor-component' : SensorComponent
        },
        created() {
            axios.get('/api/sensor').then((result) => {
                this.dataList = result.data.deviceDataList;
                this.totalDeviceNumber = result.data.totalDeviceNumber;
            });
            this.connect();
        },
        data(){
            return{
                dataList: [],
                totalDeviceNumber: 0,
            }
        },
        methods:{
            connect(){
                var socket = io('http://localhost:3000');
                socket.on('connect', function(){});
                socket.on('hi', function(data){console.log(data)});
                socket.on('disconnect', function(){});
            }
        }
        }

</script>


<style scoped>


</style>
