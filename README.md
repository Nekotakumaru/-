<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>おすすめのゲーム</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="./css/w3.css">
  <script src="js/vue.dev.js"></script>
  <style>
    body {
      background-color: #ccffcc;
      color: #333;
      font-family: "Hiragino Kaku Gothic ProN", "メイリオ", sans-serif;
    }
    .container {
      max-width: 1000px;
      margin: auto;
    }
    .game-card {
      background-color: #fff;
      border-radius: 10px;
      transition: transform 0.3s;
      cursor: pointer;
      display: flex;
      flex-direction: row;
      text-decoration: none;
      color: inherit;
      padding: 20px;
      margin: 20px 0;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    .game-card:hover {
      transform: scale(1.02);
      background-color: #f6fff6;
    }
    .left {
      flex: 1;
    }
    .right {
      flex: 1;
      padding-left: 20px;
    }
    .game-image {
      max-width: 100%;
      height: auto;
      border-radius: 8px;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div class="w3-container w3-center w3-padding-32">
    <h1 class="w3-xxlarge">🎮 おすすめのゲーム</h1>
    <p class="w3-large">人気の無料ゲームを紹介します！<br>(クリックで公式サイトへ)</p>
  </div>

  <div id="vue" class="w3-container container">
    <a
      class="game-card"
      v-for="item in list"
      :href="item.link"
      target="_blank"
      :key="item.name"
    >
      <div class="left">
        <h2>{{ item.name }}</h2>
        <img :src="item.img" alt="ゲーム画像" class="game-image">
        <h4>📅 リリース年：{{ item.price }}年</h4>

        <div v-if="item.set.length">
          <h4>⬇️ 総ダウンロード数</h4>
          <ul class="w3-ul">
            <li v-for="set in item.set">{{ Number(set.time).toLocaleString() }} 回</li>
          </ul>
          <h4>💰 料金</h4>
          <ul class="w3-ul">
            <li v-for="set in item.set">{{ set.price === 0 ? "無料" : set.price + ' 円' }}</li>
          </ul>
        </div>
      </div>
      <div class="right">
        <h3>✨ おすすめポイント</h3>
        <p>{{ item.recommend }}</p>
      </div>
    </a>
  </div>

  <script>
    new Vue({
      el: '#vue',
      data: {
        list: [
          {
            name: "原神 / miHoYo",
            price: 2020,
            img: "img/gennsinn.jpg",
            link: "https://genshin.hoyoverse.com/ja",
            recommend: "『原神』は、美しく幻想的なアニメ調のグラフィックで描かれた広大な世界を自由に探索できるアクションRPGです。山を登り、空を飛び、海を泳ぐなど、冒険の自由度が非常に高く、プレイヤーは思い思いの旅を楽しめます。バトル面では「元素反応」という戦略性の高いシステムが採用されており、水・炎・雷・氷といった属性を組み合わせて戦うことで、多様な戦術が展開可能です。さらに、豪華声優陣によるキャラクターボイスや、美しいモーションと演出によって、登場人物への愛着が自然と深まります。ソロプレイでもマルチプレイでも楽しめるため、自分のスタイルに合わせた遊び方が可能です。",
            set: [{ time: 100000000, price: 0 }]
          },
          {
            name: "Call of Duty(モバイル) / Activision Blizzard",
            price: 2003,
            img: "img/COD.jpg",
            link: "https://www.callofduty.com/ja/mobile",
            recommend: "『CODモバイル』は、人気FPSシリーズ「Call of Duty」の臨場感をスマートフォンで再現しており、高画質グラフィックと滑らかな操作性が特徴です。5対5のチーム戦やバトルロイヤルなど、多彩なモードが用意されており、短時間でも気軽に遊べます。武器のカスタマイズ要素も豊富で、自分だけの装備を作り上げる楽しさがあります。さらに、世界中のプレイヤーとリアルタイムで対戦できるため、競技性の高いプレイを求める人にも満足度の高い内容となっています。シリーズファンはもちろん、FPS初心者でも安心して始められるサポート機能も整っています。",
            set: [{ time: 500000000, price: 0 }]
          },
          {
            name: "モンスト / MIXI",
            price: 2013,
            img: "img/monnsuto.jpg",
            link: "https://www.monster-strike.com/",
            recommend: "『モンスターストライク』は、キャラクターを引っぱって弾くだけのシンプルな操作で楽しめるアクションRPGです。壁や敵に当たって跳ね返る爽快なプレイ感に加え、仲間にぶつかることで発動する「友情コンボ」など、戦略性も光ります。数千体以上のキャラクターが登場し、それぞれ固有のスキルやアビリティを持っているほか、アニメや漫画との期間限定コラボも頻繁に実施されており、ファンを飽きさせません。最大4人までの協力プレイにも対応しており、友達と力を合わせて強敵に挑む楽しさは格別です。初心者にやさしい設計も魅力の一つで、誰でもスムーズにゲームを始められる点が好評です。",
            set: [{ time: 5000000, price: 0 }]
          },
          {
            name: "Apex Legends / Respawn Entertainment",
            price: 2019,
            img: "img/APEX.jpg",
            link: "https://www.ea.com/ja-jp/games/apex-legends",
            recommend: "『Apex Legends』は、3人1組で戦うバトルロイヤル形式の基本無料FPSです。各キャラクター「レジェンド」は異なるスキルや役割を持っており、チームの戦略や連携が勝敗を左右する点が大きな魅力です。立体的な移動アクションも爽快で、テンポの早いスピーディーな戦闘が特徴です。シーズンごとのアップデートによって新たなレジェンドやマップが追加され、常に新鮮なプレイ体験が楽しめます。クロスプレイにも対応しており、PCや家庭用ゲーム機、モバイル端末など、異なるプラットフォームの友達とも気軽に一緒に遊ぶことが可能です。",
            set: [{ time: 329000000, price: 0 }]
          }
        ]
      }
    });
  </script>
</body>
</html>
# -
