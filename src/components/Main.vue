<template>
  <div id="app">
    <p></p>
    <v-container>
      <v-switch v-model="checkBox" @click="!checkBox"></v-switch>
      <v-card v-if="checkBox">
        <v-card-text>
          <v-row>
            <v-col cols="2">
              <v-text-field label="内容" required v-model="naiyou"></v-text-field>
            </v-col>
            <v-col cols="2">
              <v-text-field label="年" required v-model="year"></v-text-field>
            </v-col>
            <v-col cols="2">
              <v-text-field label="月" required v-model="month"></v-text-field>
            </v-col>
            <v-col cols="2">
              <v-text-field label="日" required v-model="day"></v-text-field>
            </v-col>
            <v-col cols="2">
              <v-text-field label="時" required v-model="hour"></v-text-field>
            </v-col>
            <v-col cols="2">
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
            <v-row  justify="center">
              <v-card-title class="headline">
                <v-col>
                  <h4><font id="font_size">{{ naiyou }}</font><font id="font_size1">まであと</font><font id="font_size2">{{this.outDay}}日</font></h4>
                </v-col>
              </v-card-title>
            </v-row>
            <v-row justify="center">
              <h2 id="font_size3">{{this.outHour}}時間{{this.outMinutes}}分{{this.outSeconds}}秒</h2>
            </v-row>
            <v-row justify="center">
              <Meigen></Meigen>
            </v-row>
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
      naiyou:"夏休み終了",
      year:2020,
      month:8,
      day:16,
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
    }
  })
</script>

<style>
  @media screen and (min-width:0px) and ( max-width:480px){
    #font_size{
      font-size: 26px;
    }

    #font_size1{
      font-size: 15px;
    }

    #font_size2{
      font-size: 42px;
    }

    #font_size3{
      font-size: 20px;
    }
  }

  @media screen and (min-width:480px) and (max-width:768px){
    #font_size{
      font-size: 26px;
    }

    #font_size1{
      font-size: 15px;
    }

    #font_size2{
      font-size: 42px;
    }

    #font_size3{
      font-size: 20px;
    }
  }

  @media screen and (min-width:768px) and ( max-width:1024px){
    #font_size{
      font-size: 30px;
    }

    #font_size1{
      font-size: 18px;
    }

    #font_size2{
      font-size: 50px;
    }

    #font_size3{
      font-size: 22px;
    }
  }

  @media screen and (min-width:1024px) and ( max-width:1400px){
    #font_size{
      font-size: 35px;
    }

    #font_size1{
      font-size: 20px;
    }

    #font_size2{
      font-size: 60px;
    }

    #font_size3{
      font-size: 25px;
    }
  }

  @media screen and (min-width:1400px){
    #font_size{
      font-size: 40px;
    }

    #font_size1{
      font-size: 25px;
    }

    #font_size2{
      font-size: 70px;
    }

    #font_size3{
      font-size: 30px;
    }
  }
</style>
