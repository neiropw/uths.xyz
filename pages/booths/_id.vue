<template>
  <main class="container">
    <h1><span>体験する</span> LANケーブル制作体験</h1>
    <p>ここに各ブースの説明文が入ります。大体２行ぐらいで収まるはずです。</p>
    <h2>このブースの詳しい説明</h2>
    <div class="row">
      <div class="column">
        <table>
          <tr>
            <th>担当</th>
            <td><span>電子情報科 2年</span></td>
          </tr>
          <tr>
            <th>場所</th>
            <td>
              <span>電気情報システム系 実習棟</span>
              <span>2階</span>
              <span>光ファイバー実習室</span>
            </td>
          </tr>
          <tr>
            <th>時間</th>
            <td><span>随時</span></td>
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
}
.column {
  width: 50%;
  float: left;
}
</style>

