<template>
  <div>
    <h1>{{ title }}</h1>
  </div>
</template>

<script>

export default {
  layout: 'page',
  head() {
    return {
      title: `${this.title} - 宇工祭Webパンフレット`
    }
  },
  data() {
    return {
      title: '会場マップ'
    }
  },
  created() {}
}

</script>

<style scoped>

</style>

