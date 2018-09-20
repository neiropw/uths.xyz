<template>
  <div>
    <header class="concept">
      <div class="concept-card">
        <div class="title">宇工祭2018</div>
        <div class="content">
          2018.11.03 (祝)<br />
          栃木県立宇都宮工業高等学校
        </div>
        <div class="theme">まだテーマすら発表されてない<br />多分直前にならないとわからないやつだこれ</div>
      </div>
    </header>
    <app-navbar />
    <nuxt/>
  </div>
</template>

<script>

import AppNavbar from "../components/AppNavbar";

export default {
  components: { AppNavbar }
}

</script>

<style scoped>

.concept {
  background: rgba(0, 0, 0, 0.5);
  text-align: center;
}
.concept-card {
    display: inline-block;
    margin: 30px; padding: 30px;
    background: #fff;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
}
    .concept-card .title { font-weight: bold; font-size: 2em; }
    .concept-card .content { color: rgb(89, 89, 89); }
    .concept-card .theme { padding: 0; padding-top: 20px; font-size: 1.75em; }

</style>

