<template>
  <div>
    <app-navbar />
    <main class="container">
      <nuxt/>
    </main>
  </div>
</template>

<script>

import AppNavbar from '../components/AppNavbar';
export default {
  components: { AppNavbar }
}

</script>
