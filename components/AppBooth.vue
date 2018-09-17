<template>
  <div class="search-card-wrap" :booth="booth">
    <a class="search-card" href="#">
      <div class="tags"><span>{{ categoryToName(booth.category) }}</span> <span>{{ booth.person.name }}</span> <span>{{ booth.place.name }}</span></div>
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