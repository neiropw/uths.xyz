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
      title: '開催概要',
    }
  },
  created() {}
}

</script>

<style scoped>

</style>

