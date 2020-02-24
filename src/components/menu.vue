<template>
    <div>
        <div class="container">
    <!--        1. 센서 확인 2. 일지 작성 3.일지 검색 -->
            <h1 @click="onSensorClick">센서 확인</h1>
            <h1 @click="onDiaryClick">일지 작성</h1>
            <h1 @click="onDiarySearch">일지 검색</h1>
        </div>
        <div>
            <h2>{{ this.data.length === 0 ? '온도' : this.data[0].sensorData.temperature}}</h2>
            <h2>{{ this.data.length === 0 ? '습도' : this.data[0].sensorData.humidity}}</h2>
            <h2>{{ this.data.length === 0 ? '조도' : this.data[0].sensorData.light}}</h2>
            <h2>{{ this.data.length === 0 ? '날짜' : this.data[0].date}}</h2>
            <h2>{{ this.data.length === 0 ? '기기' : this.data[0].device}}</h2>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: "menu-component",
        data(){
            return {
                data : []
            }
        },
        methods:{
            onSensorClick(){
              console.log('센서 클릭');
              axios.get('/api/sensor').then(result => {
                  console.log(result);
                  const newData = {
                      sensorData : result.data.sensorData,
                      device : result.data.device,
                      date : result.data.date
                  };
                  this.data = this.data.concat(newData);

                  // console.log(this.sensorData);
              });
            },
            onDiaryClick(){
                console.log('일지 클릭');
            },
            onDiarySearch(){
                console.log('일지 검색');
            }
        }
    }
</script>

<style scoped>
    .container{
        display: inline-flex;
    }
    .container > h1 {
        padding-left: 10px;
        padding-right: 10px;
    }
</style>
