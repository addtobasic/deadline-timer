<template>
  <div id="app">
    <p></p>
    <v-container>
      <v-switch v-model="checkBox" @click="!checkBox"></v-switch>
      <v-card v-if="checkBox">
        <v-card-text>
          <v-row>
            <v-col cols="2">
              <v-text-field
                label="内容"
                required
                v-model="content"
              ></v-text-field>
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
              <v-text-field
                label="分"
                required
                v-model="minutes"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-container>
    <v-container>
      <v-row dense>
        <v-col cols="12">
          <v-card>
            <v-row justify="center">
              <v-card-title class="headline">
                <v-col>
                  <h4>
                    <font id="font_size">{{ content }}</font
                    ><font id="font_size1">まであと</font
                    ><font id="font_size2">{{ this.outDay }}日</font>
                  </h4>
                </v-col>
              </v-card-title>
            </v-row>
            <v-row justify="center">
              <h2 id="font_size3">
                {{ this.outHour }}時間{{ this.outMinutes }}分{{
                  this.outSeconds
                }}秒
              </h2>
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
import Vue from "vue";
import moment from "moment";
import Meigen from "./Meigen.vue";

export default Vue.extend({
  name: "Main",
  components: {
    Meigen,
  },

  data: () => ({
    //初期値
    content: "",
    year: 2021,
    month: 1,
    day: 1,
    hour: 0,
    minutes: 0,
    seconds: 0,
    inTimeText: "",
    isTimeUp: false,
    time: 0,

    //出力の数値
    outDay: 0,
    outHour: 0,
    outMinutes: 0,
    outSeconds: 0,
    checkBox: true,
  }),
  created: function() {
    setInterval(() => {
      //入力された時間の文字列を作成
      this.inTimeText =
        this.year +
        "/" +
        this.month +
        "/" +
        this.day +
        " " +
        this.hour +
        ":" +
        this.minutes +
        ":" +
        this.seconds;

      //入力された時間と今の時間の差を計算
      var now = moment();
      var inTime = moment(this.inTimeText);
      this.time = Math.floor(inTime.diff(now) / 1000);

      //出力する形にそれぞれを変換
      this.outDay = Math.floor(this.time / (24 * 60 * 60));
      this.outHour = Math.floor((this.time % (24 * 60 * 60)) / (60 * 60));
      this.outMinutes = Math.floor(
        ((this.time % (24 * 60 * 60)) % (60 * 60)) / 60
      );
      this.outSeconds = ((this.time % (24 * 60 * 60)) % (60 * 60)) % 60;

      //時間切れになっていなかったら1秒ずつ減らす
      if (this.time > 0 && !this.isTimeUp) this.time--;
      //時間切れになったら煽る
      else if (this.time === 0 && !this.isTimeUp) {
        alert("無事期限までに間に合いましたかww");
        location.reload();
        this.isTimeUp = true;
      }

      //終了したら数値のリセット
      else if (this.time < 0) {
        this.outDay = 0;
        this.outHour = 0;
        this.outMinutes = 0;
        this.outSeconds = 0;
      }
    }, 1000);
  },

  mounted() {
    if (localStorage.content) {
      this.content = localStorage.content;
    }

    if (localStorage.year) {
      this.year = localStorage.year;
    }
    if (localStorage.month) {
      this.month = localStorage.month;
    }
    if (localStorage.day) {
      this.day = localStorage.day;
    }
    if (localStorage.hour) {
      this.hour = localStorage.hour;
    }
  },

  watch: {
    content(newContent) {
      localStorage.content = newContent;
    },

    year(newYear) {
      localStorage.year = newYear;
    },
    month(newMonth) {
      localStorage.month = newMonth;
    },
    day(newDay) {
      localStorage.day = newDay;
    },
    hour(newHour) {
      localStorage.hour = newHour;
    },
  },
});
</script>

<style>
@media screen and (min-width: 0px) and (max-width: 480px) {
  #font_size {
    font-size: 26px;
  }

  #font_size1 {
    font-size: 15px;
  }

  #font_size2 {
    font-size: 42px;
  }

  #font_size3 {
    font-size: 20px;
  }
}

@media screen and (min-width: 480px) and (max-width: 768px) {
  #font_size {
    font-size: 26px;
  }

  #font_size1 {
    font-size: 15px;
  }

  #font_size2 {
    font-size: 42px;
  }

  #font_size3 {
    font-size: 20px;
  }
}

@media screen and (min-width: 768px) and (max-width: 1024px) {
  #font_size {
    font-size: 30px;
  }

  #font_size1 {
    font-size: 18px;
  }

  #font_size2 {
    font-size: 50px;
  }

  #font_size3 {
    font-size: 22px;
  }
}

@media screen and (min-width: 1024px) and (max-width: 1400px) {
  #font_size {
    font-size: 35px;
  }

  #font_size1 {
    font-size: 20px;
  }

  #font_size2 {
    font-size: 60px;
  }

  #font_size3 {
    font-size: 25px;
  }
}

@media screen and (min-width: 1400px) {
  #font_size {
    font-size: 40px;
  }

  #font_size1 {
    font-size: 25px;
  }

  #font_size2 {
    font-size: 70px;
  }

  #font_size3 {
    font-size: 30px;
  }
}
</style>
