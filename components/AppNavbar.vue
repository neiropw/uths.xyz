<template>
  <nav class="nav">
    <ul>
      <li><a href="#" class="ms">開催概要</a></li>
      <li><a href="#" class="ei">お知らせ</a></li>
      <li><a href="#" class="bd">会場マップ</a></li>
      <li><a href="#" class="es">Webパンフレット</a></li>
    </ul>
  </nav>
</template>

<script>
</script>

<style scoped>

.nav {
  background: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
  text-align: center;
}
  .nav ul li {
    width: 25%;
    display: inline-block;
  }
  .nav ul li a {
    display: block;
    text-decoration: none;
    margin: 10px; padding: 10px;
    font-size: 1.25em;
    color: #fff;
  }
    .nav ul li a.ms { background: rgb(255, 80, 80) }
    .nav ul li a.ei { background: rgb(255, 153, 51) }
    .nav ul li a.bd { background: rgb(91, 155, 213) }
    .nav ul li a.es { background: rgb(112, 173, 71) }

</style>
