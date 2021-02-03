<template>
  <div id="homepage" >
    <div class="container">
      <div style="text-align: center;" class="notification is-primary">
        <section class="section">
          <h1 class="title">Willkommen auf der Startseite des <strong>Ledavi</strong>, dem Leonardo da Vinci Restaurant.</h1>
        </section>
      </div>
    </div>

    <b-carousel :indicator-inside="false">
      <b-carousel-item>
        <span class="image">
          <img src="~/assets/gallery-1.png" width="100" height="100">
        </span>
      </b-carousel-item>
      <b-carousel-item>
        <span class="image">
          <img src="~/assets/gallery-2.png" width="100" height="100">
        </span>
      </b-carousel-item>
      <b-carousel-item>
        <span class="image">
          <img src="~/assets/gallery-3.png" width="100" height="100">
        </span>
      </b-carousel-item>
      <b-carousel-item>
        <span class="image">
          <img src="~/assets/gallery-4.png" width="100" height="100">
        </span>
      </b-carousel-item>
    </b-carousel>

    <br><br><br>

    <div class="container">
      <div class="notification is-primary has-text-centered">
        <section class="section">
          <h1 class="title">Menü</h1>
        </section>
      </div>
    </div>

    <section class="section">
      <h1 class="title">Essen</h1>
      <h2 class="subtitle">
        <li>Spaghetti</li>
        <li>Pizza</li>
        <li>Schafskäse + Salat</li>
        <li>Krautsalat</li>
        <li>Garnelen</li>
        <li>Frikadellen</li>
        <li>Ramen</li>
        <li>Sushi</li>
      </h2>
      <h1 class="title">Trinken</h1>
      <h2 class="subtitle">
        <li>Kaffee</li>
        <li>Tee</li>
        <li>Milch</li>
      </h2>
    </section>
  </div>
</template>

<style>
#menu-items {
  font-size: 1.5em;
  margin-left: 20px;
}
p {
  font-size: 2em;
}
#homepage {
  width: 50%;
  margin-left: 25%;
}
</style>

<script>
export default {
  name: 'homepage',

  methods: {
    getImgUrl(value) {
      return `/assets/gallery-${value}.png`
    }
  }
}
</script>
