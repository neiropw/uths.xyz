<template>
  <div class="search-card-wrap" :booth="booth">
    <a class="search-card" href="#">
      <div class="tags"><span class="label label-category">{{ categoryToName(booth.category) }}</span> <span class="label label-person">{{ booth.person.name }}</span> <span class="label label-place">{{ booth.place.name }}</span></div>
      <div class="title">{{ booth.name }}</div>
      <div class="content">{{ booth.content }}</div>
    </a>
  </div>
</template>

<script>
export default {
  props: ['booth'],
  methods: {
    categoryToName(category) {
      switch(category) {
        case 'SEE':
          return '見る'
        case 'EAT':
          return '食べる'
        case 'PLAY':
          return '体験する'
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
  .search-card .title {
    padding: 5px;
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
