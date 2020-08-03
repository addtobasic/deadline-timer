<template>
  <div id="app">
    <p></p>
    <v-container>
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
        <!-- <v-btn @click="calc">make</v-btn> -->
      </v-card>
    </v-container>
    <v-container>
      <v-row dense>
        <v-col cols="12">
          <v-card>
            <v-card-title class="headline">
              <h3>{{ naiyou }}まであと{{this.outDay}}日</h3>
            </v-card-title>
            <h1>{{ calc }}</h1>
            <!-- <h1>this.time = {{this.time}}</h1> -->
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
        month:8,
        day:4,
        hour:0,
        minutes:0,
        seconds:0,
        inTime:"",
        time:0,
        outDay:0,
        outHour:0,
        outMinutes:0,
        outSeconds:0,
      }),

      created: function () {
        setInterval(() => {
          if(this.time>0)
          {
            this.inTime = this.year+"-"+this.month+"-"+this.day+" "+this.hour+":"+this.minutes+":"+this.seconds
            this.time--
            this.outDay = Math.floor(this.time / (24 * 60 * 60))
            this.outHour = Math.floor(this.time % (24 * 60 * 60) / (60 * 60));
            this.outMinutes = Math.floor(this.time % (24 * 60 * 60) % (60 * 60) / 60);
            this.outSeconds = this.time % (24 * 60 * 60) % (60 * 60) % 60;
          }
          else if(this.time===0)
          {
            alert("無事期限までに間に合いましたかww")
            this.time--
          }
          else
          {
            this.time--
            this.outDay = Math.floor(moment(this.inTime).diff(moment())/1000)+1
            this.outHour = Math.floor(this.time % (24 * 60 * 60) / (60 * 60))+1
            this.outMinutes = Math.floor(this.time % (24 * 60 * 60) % (60 * 60) / 60)+1
            this.outSeconds = this.time % (24 * 60 * 60) % (60 * 60) % 60+1
            console.log("足した結果this.outDay"+this.outDay)
            console.log("足した結果this.outHour"+this.outHour)
            console.log("足した結果outMinutes"+this.outMinutes)
            console.log("足した結果outSeconds"+this.outSeconds)
          }
          //なぜか日付だけがおかしい
          // console.log("inTime"+this.inTime)
          console.log("time"+this.time)
          console.log("outDay"+this.outDay)
          console.log("outHour"+this.outHour)
          console.log("outMinutes"+this.outMinutes)
          console.log("outSeconds"+this.outSeconds)
          }, 1000);
      },
      computed:{
        calc:function(){
          this.inTime = this.year+"-"+this.month+"-"+this.day+" "+this.hour+":"+this.minutes+":"+this.seconds
          // console.log("合計時間"+this.inTime)
          // console.log("年"+this.year)
          // console.log("月"+this.month)
          // console.log("日"+this.day)
          // console.log("時"+this.hour)
          // console.log("分"+this.minutes)
          // console.log("秒"+this.seconds)

          var now = moment();
          var from = moment(this.inTime);//inTime
          // console.log("now"+now)
          // console.log("from"+from)
          this.time = Math.floor(from.diff(now)/1000)
          var t = Math.floor(from.diff(now)/1000)
          var d = Math.floor(t / (24 * 60 * 60));
          var h = Math.floor(t % (24 * 60 * 60) / (60 * 60));
          var m = Math.floor(t % (24 * 60 * 60) % (60 * 60) / 60);
          var s = t % (24 * 60 * 60) % (60 * 60) % 60;
          if(t<0)
          {
            t = Math.floor(from.diff(now)/1000)+1
            d = Math.floor(t / (24 * 60 * 60))+1
            h = Math.floor(t % (24 * 60 * 60) / (60 * 60))+1
            m = Math.floor(t % (24 * 60 * 60) % (60 * 60) / 60)+1
            s = t % (24 * 60 * 60) % (60 * 60) % 60
          }

          // console.log("t1="+t);
          // console.log("d1="+d);
          // console.log("h1="+h);
          // console.log("m1="+m);
          // console.log("s1="+s);
          // var dhms = d + '日' + h + '時間' + m + '分' + s + '秒';
          // if(t===0&&d===0&&h===0&&m===0&&s===0)alert("無事期限までに間に合いましたかww")
          // return dhms;

        }
    },
  })
</script>
