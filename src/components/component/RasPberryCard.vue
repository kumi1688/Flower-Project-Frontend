<template>
    <v-container >
    <v-card

            class="mx-auto"
            max-width="344"
            outlined
            >
        <v-list-item-title style="text-align: center">{{pdata[pdata.length-1].device}}</v-list-item-title>
        <v-list-item three-line>
            <v-list-item-content>
                    <v-list-item-title style="padding-left: 15px">온도</v-list-item-title>
                    <v-progress-circular width="10" size="60" color="brown"
                            :value=pdata[pdata.length-1].sensorData.temperature>{{pdata[pdata.length-1].sensorData.temperature}}
                    </v-progress-circular>
            </v-list-item-content>

            <v-list-item-content>
                <v-list-item-title style="padding-left: 15px">습도</v-list-item-title>
                <v-progress-circular width="10" size="60" color="blue"
                                     :value=pdata[pdata.length-1].sensorData.humidity>{{pdata[pdata.length-1].sensorData.humidity}}
                </v-progress-circular>
            </v-list-item-content>

            <v-list-item-content>
                <v-list-item-title style="padding-left: 15px">조도</v-list-item-title>
                <v-progress-circular width="10" size="60" color="green"
                                     :value=pdata[pdata.length-1].sensorData.light>{{pdata[pdata.length-1].sensorData.light}}
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
            <v-switch
                    style="padding-left: 5px"
                    v-model="mqtt"
                    :label="`전원`"
            ></v-switch>
            <v-btn @click="onClickCamera" color="primary" style="margin-left: 15px" small>카메라</v-btn>
            <v-btn @click="onClickCardDetail" color="primary" style="margin-left: 15px" small>상세정보</v-btn>
        </v-card-actions>
    </v-card>
        <modal-component v-on:onClickCardDetail="onClickCardDetail" v-show="showModal"
                        v-bind:showModal="showModal" v-bind:pdata="pdata"></modal-component>
    </v-container>
</template>

<script>
    import ModalComponent from "./ModalComponent";
    export default {
        name: "RasPberryCard",
        components:{
            'modal-component': ModalComponent
        },
        data(){
            return{
                showModal: false,
                camera: false,
                mqtt: false,
            }
        },
        props: ['pdata'],
        methods:{
            onClickCardDetail(){
                this.showModal = !this.showModal;
            },
            onClickCamera(){
                this.camera = !this.camera;
            },
            onClickMqtt(){
                this.mqtt = !this.mqtt;
            }
        }
    }
</script>

<style scoped>

</style>
