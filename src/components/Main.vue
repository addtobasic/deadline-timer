<template>
  <div id="app">
    <p></p>
    <v-container v-if="checkBox">
      <v-card>
        <v-card-text>
          <v-row>
            <v-col cols="4">
              <v-text-field label="締切の内容" required v-model="naiyou"></v-text-field>
            </v-col>
            <v-col cols="1">
              <v-text-field label="年" required v-model="year"></v-text-field>
            </v-col>
            <v-col cols="1">
              <v-text-field label="月" required v-model="month"></v-text-field>
            </v-col>
            <v-col cols="1">
              <v-text-field label="日" required v-model="day"></v-text-field>
            </v-col>
            <v-col cols="1">
              <v-text-field label="時" required v-model="hour"></v-text-field>
            </v-col>
            <v-col cols="1">
              <v-text-field label="分" required v-model="minutes"></v-text-field>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-container>
    <v-container>
      <v-row dense>
        <v-col cols="12">
          <v-card>
            <v-switch v-model="checkBox" @click="!checkBox"></v-switch>
            <v-card-title class="headline">
              <h3>{{ naiyou }}まであと{{this.outDay}}日</h3>
            </v-card-title>
            <h1>{{this.outHour}}時間{{this.outMinutes}}分{{this.outSeconds}}秒</h1>
          <Meigen></Meigen>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import moment, { min } from 'moment';
  import Meigen from './Meigen.vue'

  export default Vue.extend({
    name: 'Main',
    components:{
      Meigen,
    },

    data:()=>({
      naiyou:"レポート提出",
      year:2020,
      month:1,
      day:1,
      hour:0,
      minutes:0,
      seconds:0,
      inTime:"",
      timeFlag:true,
      time:0,
      time1:0,
      outDay:0,
      outHour:0,
      outMinutes:0,
      outSeconds:0,
      checkBox:true,
    }),

    created: function () {
      setInterval(() => {

        this.inTime = this.year+"-"+this.month+"-"+this.day+" "+this.hour+":"+this.minutes+":"+this.seconds
        var now = moment();
        var from = moment(this.inTime);
        this.time = Math.floor(from.diff(now)/1000)

        if(this.time===0 && this.timeFlag)
        {
          alert("無事期限までに間に合いましたかww")
          location.reload()
          this.timeFlag = false
        }

        if(this.time>0&&this.timeFlag)this.time--

        this.inTime = this.year+"-"+this.month+"-"+this.day+" "+this.hour+":"+this.minutes+":"+this.seconds
        this.outDay = Math.floor(this.time / (24 * 60 * 60))
        this.outHour = Math.floor(this.time % (24 * 60 * 60) / (60 * 60));
        this.outMinutes = Math.floor(this.time % (24 * 60 * 60) % (60 * 60) / 60);
        this.outSeconds = this.time % (24 * 60 * 60) % (60 * 60) % 60;
        if(this.time<0)
        {
          this.outDay = 0
          this.outHour = 0
          this.outMinutes = 0
          this.outSeconds = 0
        }
      }, 1000);
    },
  })
</script>
