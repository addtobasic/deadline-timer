<template>
  <div id="app">
    <v-row id="center" justify="center">
    <v-card>
        <v-card-text>
          <v-container>
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
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn  color="blue darken-1">Make</v-btn>
        </v-card-actions>
      </v-card>
    </v-row>
    <p>{{ naiyou }}まであと</p>
    <h1>{{ calc }}</h1>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import moment, { min } from 'moment';

  export default Vue.extend({
    name: 'Main',
      data:()=>({
        naiyou:"レポート提出",
        year:2020,
        month:8,
        day:3,
        hour:0,
        minutes:0,
        seconds:0,
        inTime:""
      }),

      created: function () {
        setInterval(() => { this.inTime-- }, 1000);
      },
      computed:{
        calc:function(){
          this.inTime = this.year+"-"+this.month+"-"+this.day+" "+this.hour+":"+this.minutes+":"+this.seconds
          console.log("合計時間"+this.inTime)
          console.log("年"+this.year)
          console.log("月"+this.month)
          console.log("日"+this.day)
          console.log("時"+this.hour)
          console.log("分"+this.minutes)
          console.log("秒"+this.seconds)

          const now = moment();
          const from = moment(this.inTime);//inTime

          var t = Math.floor(from.diff(now)/1000)
          var d = Math.floor(t / (24 * 60 * 60));
          var h = Math.floor(t % (24 * 60 * 60) / (60 * 60));
          var m = Math.floor(t % (24 * 60 * 60) % (60 * 60) / 60);
          var s = t % (24 * 60 * 60) % (60 * 60) % 60;
          if(t<0)
          {
            var t = Math.floor(from.diff(now)/1000)+1
            var d = Math.floor(t / (24 * 60 * 60))+1
            var h = Math.floor(t % (24 * 60 * 60) / (60 * 60))+1
            var m = Math.floor(t % (24 * 60 * 60) % (60 * 60) / 60)+1
            var s = t % (24 * 60 * 60) % (60 * 60) % 60+1
          }
          function check(v: number)
          {
            if (v < 10)return "0" + v;
            else return v;
          }

          console.log("t1="+t);
          console.log("h1="+h);
          console.log("m1="+m);
          console.log("s1="+s);
        // setInterval(() => {


        //   }, 1000);
          var dhms = d + '日' + h + '時間' + m + '分' + s + '秒';
          if(d===0&&h===0&&m===0&&s===0)
          {
            alert("無事期限までに間に合いましたかww")
            d=0
            h=0
            m=0
            s=-1
          }
          return dhms;
        }
    },
  })
</script>
