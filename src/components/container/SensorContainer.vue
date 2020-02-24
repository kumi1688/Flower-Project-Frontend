<template>
    <v-container>
        <sensor-component v-bind:dataList="dataList"></sensor-component>
    </v-container>
</template>

<script>
import axios from 'axios';
import SensorComponent from "../component/SensorComponent";

    export default {
        name: "Sensor",
        components:{
            'sensor-component' : SensorComponent
        },
        created() {
            axios.get('/api/sensor').then((result) =>{
                result.data.map(element=> {
                    this.dataList = this.dataList.concat({
                        sensorData: element.sensorData,
                        date: element.date,
                        device: element.device,
                        _id: element._id
                    })
                });
            });
        },
        data(){
            return{
                dataList: [],
            }
        }
    }
</script>


<style scoped>


</style>
