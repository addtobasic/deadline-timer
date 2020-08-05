<template>
  <div>
    <div id="card_width">
    <v-card-text>
      <h2>{{item[rand].text}}</h2>
        </v-card-text>
        <v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <h4>{{item[rand].person}}</h4>
          </v-card-actions>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn @click="changeMeigen" color="primary">change</v-btn>
          </v-card-actions>
        </v-card-text>
    </div>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  export default Vue.extend({
    name: 'Meigen',
    data() {
      return {
        rand:Math.floor(Math.random()*30),
        item:
      [
        {
          text:'この地上で過ごせる時間には限りがあります。本当に大事なことを本当に一生懸命できる機会は、二つか三つくらいしかないのです。',
          person:'スティーブ・ジョブズ'
        },
        {
          text:'人生とは今日一日のことである。',
          person:'デール・カーネギー'
        },
        {
          text:'お前がいつの日か出会う禍は、お前がおろそかにしたある時間の報いだ。',
          person:'ナポレオン・ボナパルト'
        },
        {
          text:'時間の使い方は、そのままいのちの使い方になる。',
          person:'渡辺和子'
        },
        {
          text:'今日という一日は、明日という日の二日分の値打ちがある。',
          person:'ベンジャミン・フランクリン'
        },
        {
          text:'うまく使えば、時間はいつも十分にある。',
          person:'ゲーテ'
        },
        {
          text:'時間だけは神様が平等に与えて下さった。これをいかに有効に使うかはその人の才覚であって、うまく利用した人がこの世の中の成功者なんだ。',
          person:'本田宗一郎'
        },
        {
          text:'朝7時に起き、夜11時に就寝すれば、たっぷり16時間ある。大抵の人は一日中なにか仕事をしている。ただ一つ違うのは、彼らの仕事は非常に多岐にわたり、私はたった一つの仕事に全てのエネルギーを集中する点だ。',
          person:'トーマス・エジソン'
        },
        {
          text:'たいていの成功者は他人が時間を浪費している間に先へ進む。これは私が長年、この眼で見てきたことである。',
          person:'ヘンリー・フォード'
        },
        {
          text:'何をするにも時間は見つからないだろう。時間が欲しければ自分で作ることだ。',
          person:'チャールズ・バクストン'
        },
        {
          text:'時間こそは、最もユニークで乏しい資源。',
          person:'ピーター・ドラッカー'
        },
        {
          text:'時間の使い方の最も下手なものが、まずその短さについて苦情を言う。',
          person:'ラ・ブリュイエール'
        },
        {
          text:'あなたに時間がどれだけあるかというのは問題ではない。むしろ、時間をどう使うかが問題なのだ。',
          person:'ケリー・グリーソン'
        },
        {
          text:'過去も未来も存在せず、あるのは現在と言う瞬間だけだ。',
          person:'トルストイ'
        },
        {
          text:'ぐずぐずしている間に、人生は一気に過ぎ去っていく。',
          person:'セネカ'
        },
        {
          text:'学ぶのに、時間を費やしすぎるのは、怠惰である。',
          person:'フランシス・ベーコン'
        },
        {
          text:'流れ進むのはわれわれであって、時ではない。',
          person:'トルストイ'
        },
        {
          text:'時間を最も有効に利用した者に、最も立派な仕事ができる。',
          person:'嘉納治五郎'
        },
        {
          text:'人類永遠の課題は、起きている時間をどのように構成するかだ。',
          person:'エリック・バーン'
        },
        {
          text:'短い人生は時間の浪費によっていっそう短くなる。',
          person:'サミュエル・ジョンソン'
        },
        {
          text:'あなたが持っている最大の資源は時間なのです。',
          person:'ブライアン・トレーシー'
        },
        {
          text:'究極の成功とは、自分のしたいことをする時間を自分に与える贅沢である。',
          person:'レオタイン・プライス'
        },
        {
          text:'明日はなんとかなると思う馬鹿者。今日でさえ遅すぎるのだ。賢者はもう昨日済ましている。',
          person:'チャールズ・クーリー'
        },
        {
          text:'時間がないというのは嘘である。時間は十分過ぎるほどある。',
          person:'リチャード・コッチ'
        },
        {
          text:'時間を浪費するな、人生は時間の積み重ねなのだから。',
          person:'ベンジャミン・フランクリン'
        },
        {
          text:'人は多くの時間を無駄にしている。誰もが、時間など無限にあるかのように振る舞っているが、実際には時間こそ限りある資源であり、人はそれを上手に活用していない',
          person:'ダニエル・カーネマ'
        },
        {
          text:'今日できることを明日にしてはいけない。遅延は時間の泥棒だからだ。',
          person:'チャールズ・ディケンズ'
        },
        {
          text:'賢い人間は時間を無駄にすることに最も腹が立つ',
          person:'ダンテ'
        },
        {
          text:'人生を大事にしているなら、時間を浪費してはいけない。人生は時間の積み重ねなのだから。',
          person:'ブルース・リー'
        },
        {
          text:'一時間の浪費をなんとも思わない人は、人生の価値をまだ発見してはいない。',
          person:'ダーウィン'
        }
      ],
      }
    },
    methods:{
      changeMeigen(){
        this.rand = Math.floor(Math.random()*30)
      }
    }
  })
</script>
<style>

    @media screen and (min-width:0px) and ( max-width:480px){
  #card_width
  {
    width: 320px;
  }

  }

  @media screen and (min-width:480px) and (max-width:768px){
  #card_width
  {
    width: 400px;

  }
  }

  @media screen and (min-width:768px) and ( max-width:1024px){
  #card_width
  {
    width: 480px;
  }
  }

  @media screen and (min-width:1024px) and ( max-width:1400px){
    #card_width
    {
    width: 560px;
    }
  }

  @media screen and (min-width:1400px){
    #card_width
    {
      width: 640px;
    }
  }
</style>
