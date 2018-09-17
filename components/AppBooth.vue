<template>
  <div class="search-card-wrap" :booth="booth">
    <a class="search-card" href="#">
      <div class="tags">
        <span class="label label-category">{{ categoryToName(booth.category) }}</span>
        <span class="label label-person">{{ booth.person.name }}</span>
        <span class="label label-place">{{ placeCategoryToName(booth.place.category) }}{{ booth.place.floor !== null ? ` ${booth.place.floor}階` : '' }}</span>
      </div>
      <div class="card-content">
        <div class="title">{{ booth.name }}</div>
        <div class="content">{{ booth.content }}</div>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  props: ['booth'],
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
  }
}
</script>

<style scoped>
.search-card-wrap {
  display: inline-block;
  vertical-align: top;
  width: 50%;
  padding: 10px;
}
.search-card {
  display: block;
  padding: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
  text-decoration: none;
  color: #000;
}
  .search-card .card-content { margin: 5px; }
  .search-card .card-content .title {
    font-size: 1.75em;
  }
.label {
  display: inline-block;
  margin: 0 5px;
  padding: 5px;
  font-size: 0.95em;
}
  .label-category { margin-left: 0; background: rgb(255, 80, 80); color: #fff; }
  .label-person { background: rgb(255, 153, 51); color: #fff; }
  .label-place { background: rgb(91, 155, 213); color: #fff; }
</style>
