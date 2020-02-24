<template>
    <v-row justify="center">
        <v-dialog v-model="showModal" max-width="500px">
            <v-card>
                <v-card-title>상세 정보</v-card-title>
                <v-divider></v-divider>
                <v-card-text>
                    <v-simple-table>
                        <template v-slot:default>
                            <thead>
                            <tr>
                                <th class="text-left">시간</th>
                                <th class="text-left">온도</th>
                                <th class="text-left">습도</th>
                                <th class="text-left">조도</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="data in pdata" :key=data.key>
                                <td>{{ data.date }}</td>
                                <td>{{ data.sensorData.temperature }}</td>
                                <td>{{ data.sensorData.humidity }}</td>
                                <td>{{ data.sensorData.light }}</td>
                            </tr>
                            </tbody>
                        </template>
                    </v-simple-table>


                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions >
                    <v-btn @click="clickClose" color="blue darken-1" text >Close</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-row>
</template>

<script>
    export default {
        name: "ModalComponent",
        props:['pdata', 'showModal'],
        data(){
            return{
                dialogm1: '',
                dialog: false,
            }
        },
        methods:{
            clickClose(){
                this.$emit('onClickCardDetail');
            }
        }
    }
</script>

<style scoped>

</style>
