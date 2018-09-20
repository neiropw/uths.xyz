<template>
  <main class="container">
    <div class="booth-title">
      <span class="label label-category">体験する</span>
      <h1 class="booth-name">LANケーブル制作体験</h1>
    </div>
    <p class="booth-detail">
      ここに各ブースの説明文が入ります。大体２行ぐらいで収まるはずです。
    </p>
    <h2 class="booth-info">このブースの詳しい説明</h2>
    <div class="row">
      <div class="column">
        <table class="info">
          <tr>
            <th>担当</th>
            <td><span class="label label-person">電子情報科 2年</span></td>
          </tr>
          <tr>
            <th>場所</th>
            <td>
              <span class="label label-place">電気情報システム系 実習棟 2階 光ファイバー実習室</span>
            </td>
          </tr>
          <tr>
            <th>時間</th>
            <td><span class="label label-time">随時</span></td>
          </tr>
        </table>
      </div>
      <div class="column">
        <table>
          <tr>
            <th>備考</th>
            <td>
              <ul>
                <li>身構えなくても大丈夫です</li>
                <li>作ったLANケーブルは持ち帰れます</li>
              </ul>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </main>
</template>

<script>

import axios from 'axios'

export default {
  layout: 'booth',
  data() {
    return {
      booths: []
    }
  },
  created() {
    axios.get('http://localhost:3001/booths')
      .then(res => {
        console.log(res)
        res.data.booths.forEach(booth => {
        this.booths.push(booth)
        })
        console.log(this.booths)
      })
  }
}

</script>

<style scoped>
.container { }
.row {
  overflow: hidden;
  padding: 20px;
}
  .row table { font-size: 1.25em; }
  .row table th, .row table td { padding: 5px; }
  .row table th { font-weight: normal; color: #888; }
  .row table td li::before { content: '・'; }
  .row table td li { list-style: none; }
.column {
  width: 50%;
  float: left;
}
.label {
  display: inline-block;
  vertical-align: middle;
  margin: 0 5px;
  padding: 5px;
  font-size: 0.95em;
  font-weight: bold;
}
  .label-category { margin-left: 0; background: rgb(255, 80, 80); color: #fff; }
  .label-person { background: rgb(255, 153, 51); color: #fff; }
  .label-place { background: rgb(91, 155, 213); color: #fff; }
  .label-time { background: rgb(112, 173, 71); color: #fff; }
.booth-title { border-bottom: 1px solid rgb(255, 80, 80); }
.booth-name {
  display: inline-block;
  vertical-align: middle;
  font-weight: normal;
  color: rgb(255, 80, 80);
}
.booth-info {
  font-weight: bold;
  color: rgb(255, 153, 51);
  border-bottom: 1px solid rgb(255, 153, 51);
}
.booth-detail {
  padding: 20px;
}
</style>

