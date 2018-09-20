<template>
  <div>
    <div v-if="alerts">
      <div
        v-for="(alert, index) in alerts"
        :key="index">{{ alert.title }}</div>
    </div>
    <div v-if="isReady">
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
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  layout: 'page',
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
  head() {
    return {
      title: `${this.title} - 宇工祭Webパンフレット`
    }
  },
  data() {
    return {
      title: '',
      isReady: false,
      alerts: [],
      booth: {
        id: 'booth.id',
        name: 'booth.name',
        category: 'booth.category',
        content: 'booth.content',
        remarks: [
          'booth.remarks'
        ],
        person: {
          id: 'booth.person.id',
          category: 'booth.person.category',
          name: 'booth.person.name'
        },
        place: {
          id: 'booth.place.id',
          category: 'booth.place.category',
          floor: 'booth.place.floor',
          name: 'booth.place.name'
        }
      }
    }
  },
  created() {
    if(this.$route.params.id !== undefined) {
      axios.get(`http://localhost:3001/booths/${this.$route.params.id}`)
        .then(res => {
          if(res.status === 200 && res.data.booth) {
            // console.log(res)
            this.booth = res.data.booth
            this.title = `${res.data.booth.name}(${res.data.booth.person.name})`
            this.isReady = true
            // console.log(this.booth)
          } else {
            this.alerts.push({
              title: '見つかりません！',
              content: 'お探しのブースは、Web版パンフレットに登録されていません。'
            })
            this.title = '見つかりません'
          }
        })
      return
    }
    this.alerts.push({
      title: '見つかりません！',
      content: 'お探しのブースは、Web版パンフレットに登録されていません。'
    })
    this.title = '見つかりません'
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

