<template>
  <main class="container">
    <h1 class="page-header">宇工祭パンフレット on WEB<small> powered by neiro.pw</small></h1>
    <form class="search">
      <span>
        <select class="ms">
          <option>すべての分類</option>
          <option>見る</option>
          <option>食べる</option>
          <option>体験する</option>
        </select>
      </span>
      <span>
        <select class="ei">
          <option>すべての場所</option>
          <optgroup label="実習棟">
            <option>機械システム系</option>
            <option>電気情報システム系</option>
            <option>建築デザイン系</option>
            <option>環境建設システム系</option>
          </optgroup>
          <option>普通教室棟</option>
          <option>管理・特別教室棟</option>
          <option>インタラクティブコート(中庭)</option>
          <option>校庭</option>
          <option>第一アリーナ</option>
          <option>第二アリーナ</option>
        </select>
      </span>
      <span>
        <select class="bd">
          <option>すべての担当</option>
          <option>機械システム系</option>
          <option>電気情報システム系</option>
          <option>建築デザイン系</option>
          <option>環境建設システム系</option>
          <option>有志(部活動・生徒会・PTA)</option>
        </select>
      </span>
      <span class="button">
        <button class="es">検索</button>
      </span>
    </form>
    <section class="search-result">

      <app-booth 
        v-for="(booth, index) in booths"
        :key="index"
        :booth="booth"/>

    </section>
  </main>
</template>

<script>

import axios from 'axios'

import AppBooth from '../components/AppBooth'

export default {
  components: { AppBooth },
  layout: 'home',
  data() {
    return {
      booths: []
    }
  },
  created() {
    axios.get('http://localhost:3001/booths')
      .then(res => {
        // console.log(res)
        res.data.booths.forEach(booth => {
          this.booths.push(booth)
        })
        // console.log(this.booths)
      })
  }
}

</script>

<style scoped>
*:focus {
  outline: none;
}

form.search {
  width: 100%;
  display: table;
  padding: 20px 0;
}
.search span {
  display: table-cell;
  width: 25%;
  padding: 10px;
}
.search span select, .search span.button button {
  display: inline-block;
  padding: 5px;
  width: 100%;
  font-size: 1.4em;
  height: 3rem;
  border: none;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
}
.search span select.ms { background: rgb(255, 80, 80); color: #fff; }
.search span select.ei { background: rgb(255, 153, 51); color: #fff; }
.search span select.bd { background: rgb(91, 155, 213); color: #fff; }
.search span button.es { background: rgb(112, 173, 71); color: #fff; }

.search-result {
  width: 100%;
  padding: 20px;
}
</style>

