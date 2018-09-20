<template>
  <main class="container">
    <div class="booth-title">
      <span class="label label-category">{{ categoryToName(booth.category) }}</span>
      <h1 class="booth-name">{{ booth.name }}</h1>
    </div>
    <p class="booth-detail">
      {{ booth.content !== null ? booth.content : '説明はブースで行います！　ぜひお立ち寄りください！' }}
    </p>
    <h2 class="booth-info">このブースの詳しい説明</h2>
    <div class="row">
      <div class="column">
        <table class="info">
          <tr>
            <th>担当</th>
            <td><span class="label label-person">{{ booth.person.name }}</span></td>
          </tr>
          <tr>
            <th>場所</th>
            <td>
              <span class="label label-place">{{ placeCategoryToName(booth.place.category) }}{{ booth.place.floor !== null ? ` ${booth.place.floor}階` : '' }}</span>
            </td>
          </tr>
        </table>
      </div>
      <div class="column">
        <table>
          <tr>
            <th>備考</th>
            <td>
              <ul>
                <li v-for="(remark, index) in booth.remarks" :key="index">{{ remark }}</li>
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
  methods: {
    categoryToName(category) {
      switch(category) {
        case 'SEE': return '見る'
        case 'EAT': return '食べる'
        case 'PLAY': return '体験する'
        default: return category
      }
    },
    placeCategoryToName(placeCategory) {
      switch(placeCategory) {
        case 'MS': return '機械システム系 実習棟'
        case 'EI': return '電気情報システム系 実習棟'
        case 'BD': return '建築システム系 実習棟'
        case 'ES': return '環境建設システム系 実習棟'
        case 'RC': return '普通教室棟'
        case 'SC': return '管理・特別教室棟'
        case 'IC': return 'インタラクティブコート(中庭)'
        case 'SY': return '校庭'
        case 'AR1': return '第一アリーナ'
        case 'AR2': return '第二アリーナ'
        default: return placeCategory
      }
    }
  },
  data() {
    return {
      booth: {
        id: 1,
        name: 'ミニ新幹線(E5系)の試乗体験',
        category: 'PLAY',
        content: null,
        remarks: [
          '機械システム系 実習棟 西通路(外の駐輪場寄り)で行っております。'
        ],
        person: {
          id: 1,
          category: 'MS',
          name: '機械科'
        },
        place: {
          id: 1,
          category: 'MS',
          floor: 1,
          name: null
        },
        'times': null
      }
    }
  },
  created() {
    // axios.get('http://localhost:3001/booths')
    //   .then(res => {
    //     console.log(res)
    //     res.data.booths.forEach(booth => {
    //     this.booths.push(booth)
    //     })
    //     console.log(this.booths)
    //   })
  }
}

</script>

<style scoped>

.row table { font-size: 1.25em; }
.row table th, .row table td { padding: 5px; }
.row table th { font-weight: normal; color: #888; }
.row table td li::before { content: '・'; }
.row table td li { list-style: none; }

.label { vertical-align: middle; font-weight: bold; }

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

