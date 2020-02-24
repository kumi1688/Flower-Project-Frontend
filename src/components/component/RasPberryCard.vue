<template>
    <v-card
            class="mx-auto"
            max-width="344"
            outlined
    >
        <v-list-item-title style="text-align: center">{{pdata.device}}</v-list-item-title>
        <v-list-item three-line>
            <v-list-item-content>
                    <v-list-item-title style="padding-left: 15px">온도</v-list-item-title>
                    <v-progress-circular width="10" size="60" color="brown"
                            :value=pdata.sensorData.temperature>{{pdata.sensorData.temperature}}
                    </v-progress-circular>
            </v-list-item-content>

            <v-list-item-content>
                <v-list-item-title style="padding-left: 15px">습도</v-list-item-title>
                <v-progress-circular width="10" size="60" color="blue"
                                     :value=pdata.sensorData.humidity>{{pdata.sensorData.humidity}}
                </v-progress-circular>
            </v-list-item-content>

            <v-list-item-content>
                <v-list-item-title style="padding-left: 15px">조도</v-list-item-title>
                <v-progress-circular width="10" size="60" color="green"
                                     :value=pdata.sensorData.light>{{pdata.sensorData.light}}
                </v-progress-circular>
            </v-list-item-content>

            <v-list-item-avatar
                    tile
                    size="80"
                    color="grey"
            >
                <img src="../../../public/flower.jpg" alt=""/>

            </v-list-item-avatar>
        </v-list-item>

        <v-card-actions>
            <v-btn text>Button</v-btn>
            <v-btn text>Button</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
        name: "RasPberryCard",
        props: ['pdata'],
    }
</script>

<style scoped>

</style>
