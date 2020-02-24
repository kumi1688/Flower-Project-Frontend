<template>
    <v-container>
        <sensor-component></sensor-component>
    </v-container>
</template>

<script>
import SensorComponent from "../component/SensorComponent";

    export default {
        name: "Sensor",
        components:{
            'sensor-component' : SensorComponent
        }
    }
</script>

<style scoped>


</style>
