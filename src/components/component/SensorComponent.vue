<template>
    <v-container v-if="this.dataList.length !== 0">
<!--        <ul>-->
<!--            <v-list-item v-for="data in dataList" v-bind:key="data._id">-->
<!--                <v-list-item-content style="width: 20%">-->
<!--                    <v-list-item-title>온도</v-list-item-title>-->
<!--                </v-list-item-content>-->
<!--                <v-list-item-action style="width: 90%">-->
<!--                    <v-progress-circular-->
<!--                            width="10"-->
<!--                            size="60"-->
<!--                            :value=data.sensorData.temperature>{{data.sensorData.temperature}}</v-progress-circular>-->
<!--                </v-list-item-action>-->
<!--                <v-list-item-content style="width: 20%">-->
<!--                    <v-list-item-title>습도</v-list-item-title>-->
<!--                </v-list-item-content>-->
<!--                <v-list-item-action style="width: 90%">-->
<!--                    <v-progress-circular-->
<!--                            width="10"-->
<!--                            size="60"-->
<!--                            :value=data.sensorData.humidity>{{data.sensorData.humidity}}</v-progress-circular>-->
<!--                </v-list-item-action>-->
<!--                <v-list-item-content style="width: 20%">-->
<!--                    <v-list-item-title>조도</v-list-item-title>-->
<!--                </v-list-item-content>-->
<!--                <v-list-item-action style="width: 90%">-->
<!--                    <v-progress-circular-->
<!--                            width="10"-->
<!--                            size="60"-->
<!--                            :value=data.sensorData.light>{{data.sensorData.light}}</v-progress-circular>-->
<!--                </v-list-item-action>-->
<!--            </v-list-item>-->
<!--        </ul>-->
        <ul>
            <v-container>
                <v-row>
                    <v-col v-for="rowData in dataList" :key="rowData.key">
    <!--                    <v-col  v-for="colData in rowData" :key="colData.key">-->
                                <ras-p-berry-card v-bind:pdata="rowData"></ras-p-berry-card>
    <!--                    </v-col>-->
                    </v-col>
                </v-row>
            </v-container>
        </ul>

    </v-container>
</template>

<script>
import RasPberryCard from "./RasPberryCard";

 export default {
        name: "SensorContainer",
        props: ['dataList', 'totalDeviceNumber'],
        components:{
          'ras-p-berry-card' : RasPberryCard
        },

    }
</script>

<style scoped>
    rasp {
        display: inline-flex;
    }
</style>
