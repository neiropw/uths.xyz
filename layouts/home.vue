<template>
  <div>
    <header class="concept">
      <div class="card">
        <div class="title">宇工祭2018</div>
        <div class="content">
          2018.11.03 (祝)<br />
          栃木県立宇都宮工業高等学校
        </div>
        <div class="theme">まだテーマすら発表されてない<br />多分直前にならないとわからないやつだこれ</div>
      </div>
    </header>
    <nav class="nav">
      <ul>
        <li><a href="#" class="ms">開催概要</a></li>
        <li><a href="#" class="ei">お知らせ</a></li>
        <li><a href="#" class="bd">会場マップ</a></li>
        <li><a href="#" class="es">Webパンフレット</a></li>
      </ul>
    </nav>
    <nuxt/>
  </div>
</template>

<style>
* {
  margin: 0; padding: 0;
  box-sizing: border-box;
}
html {
  width: 100%; height: 100%;
  margin: 0; padding: 0;
  background-repeat: no-repeat;
    background-position: center;
    background-attachment: fixed;
    background-size: cover;
    background-image: url('/bg.jpg');
}
small {
  font-size: 1rem;
}
.concept {
  background: rgba(0, 0, 0, 0.5);
  text-align: center;
}
.concept .card {
  display: inline-block;
  margin: 30px; padding: 30px;
  background: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
}
  .concept .card .title { font-weight: bold; font-size: 2em; }
  .concept .card .content { color: rgb(89, 89, 89); }
  .concept .card .theme { padding: 0; padding-top: 20px; font-size: 1.75em; }

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

.container {
  width: 90%;
  margin: 50px auto;
    margin-bottom: 0;
  padding: 20px;
  background: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
}
  .container .page-header {
    font-weight: normal;
    font-size: 2em;
    text-align: center;
  }

</style>

