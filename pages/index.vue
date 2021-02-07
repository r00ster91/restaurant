<template>
<div id="homepage">
  <div class="container">
    <div class="notification is-primary has-text-centered">
      <section class="section">
        <h1 class="title">
          Willkommen auf der Startseite des <strong>Ledavi</strong>, dem
          Leonardo da Vinci Restaurant.
        </h1>
      </section>
    </div>
  </div>

  <section class="hero">
    <div class="hero-body">
      <p class="title has-text-centered">
        Lassen Sie sich verführen von diesem einzigartigen französischen
        Restaurant. Unsere Kunden sind begeistert:
      <figure>
        <figcaption style="font-style: italic; font-size: 1.25em; width: 610px" class="box">
          ,,Also ich war ja wirklich schon überall, aber dieses Restaurant
          übertrifft alles."
        </figcaption>
      </figure>
      ーAleron Abadie
      <br /><br />
      <figure>
        <figcaption style="font-style: italic; font-size: 1.25em; width: 610px" class="box">
          ,,Wunderschöne Atmosphäre und ausgezeichnetes Essen."
        </figcaption>
      </figure>
      ーClaudette Roche
      <br /><br />
      <figure>
        <figcaption style="font-style: italic; font-size: 1.25em; width: 610px" class="box">
          ,,Nichts macht mich glücklicher als ein Besuch bei Ledavi."
        </figcaption>
      </figure>
      ーGarland Lavigne
      </p>
    </div>
  </section>
  <b-carousel :indicator-inside="false">
    <b-carousel-item>
      <span class="image">
        <img src="~/assets/gallery-1.png" width="100" height="100" />
      </span>
    </b-carousel-item>
    <b-carousel-item>
      <span class="image">
        <img src="~/assets/gallery-2.png" width="100" height="100" />
      </span>
    </b-carousel-item>
    <b-carousel-item>
      <span class="image">
        <img src="~/assets/gallery-3.png" width="100" height="100" />
      </span>
    </b-carousel-item>
    <b-carousel-item>
      <span class="image">
        <img src="~/assets/gallery-4.png" width="100" height="100" />
      </span>
    </b-carousel-item>
  </b-carousel>

  <br /><br /><br />

  <div class="container">
    <div class="notification is-primary has-text-centered">
      <section class="section">
        <h1 class="title">Menü</h1>
      </section>
    </div>
    <h1 class="subtitle has-text-centered">
      <NuxtLink to="/bestellen">Tätigen Sie hier Bestellungen online</NuxtLink>
    </h1>
  </div>

  <section class="section">
    <h1 class="title">Essen</h1>
    <h2 class="subtitle">
      <div v-for="item of food" :key="item" class="container">
        <li>{{ item }}</li>
      </div>
    </h2>
    <h1 class="title">Trinken</h1>
    <h2 class="subtitle">
      <div v-for="item of drinks" :key="item" class="container">
        <li>{{ item }}</li>
      </div>
    </h2>
  </section>
</div>
</template>

<style>
p {
  font-size: 2em;
}

#homepage {
  width: 50%;
  margin-left: 25%;
}

body {
  background-image: linear-gradient(90deg,
      #c850c0,
      white 33%,
      white 33%,
      white 66%,
      white 66%,
      #c850c0);
}
</style>

<script>
'use strict';

export default {
  data() {
    return {
      food: [
        'Schafskäse + Salat',
        'Krautsalat',
        'Garnelen',
        'Frikadellen',
        'Coq au Vin',
        'Croissant',
        'Baguette',
        'Französischer Käse',
        'Cassoulet',
        'Flammkuchen',
        'Foie gras',
        'Spaghetti',
        'Pizza',
        'Ramen',
        'Sushi',
      ],
      drinks: [
        'Rotwein',
        'Kir',
        'Kaffee',
        'Tee',
        'Milch'
      ],
    };
  },
  head() {
    return {
      title: 'Ledavi',
    };
  },
};
</script>
