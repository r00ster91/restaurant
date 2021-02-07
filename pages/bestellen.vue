<template>
<section class="section box">
  <p style="font-size: 1.5em">
    Hier können Sie direkt online Ihre Bestellungen tätigen.
  </p>
  <h1 class="title">Bestellungen</h1>
  <h2 class="subtitle">
    <div v-if="orders.length == 0">
      <li>
        Momentan sind keine Bestellungen aufgegeben.
      </li>
    </div>
    <div v-else-if>
      <div v-for="order of orders" class="container">
        <li>
          {{ order[0] }} (<strong>x{{ order[1] }}</strong>): bereit in: <strong>{{ order[2] }}</strong> Sekunden
        </li>
      </div>
    </div>
  </h2>
  <h1 class="title">Essen</h1>
  <h2 class="subtitle">
    <div v-for="item of food" class="container">
      <li>{{ item }}</li>
      <section>
        <b-field>
          <b-numberinput style="width: 150px;" v-model="numberPlaceholder" placeholder="1" :min="1" :max="10" size="is-small"></b-numberinput>
        </b-field>
        <b-button @click="order(item, numberPlaceholder)" type="is-success is-light">Bestellen</b-button>
      </section>
    </div>
  </h2>
  <h1 class="title">Trinken</h1>
  <h2 class="subtitle">
    <div v-for="item of drinks" class="container">
      <li>{{ item }}</li>
      <section>
        <b-field>
          <b-numberinput style="width: 150px;" v-model="numberPlaceholder" placeholder="1" :min="1" :max="10" size="is-small"></b-numberinput>
        </b-field>
        <b-button @click="order(item, numberPlaceholder)" type="is-success is-light">Bestellen</b-button>
      </section>
    </div>
  </h2>
</section>
</template>

<script>
'use strict';

export default {
  data() {
    return {
      numberPlaceholder: 1,

      // NOTE: copied from index.vue.
      // boilerplate code can be avoided here by accessing index.vue's data
      // but I'm currently not sure how to that.
      // For the time being this is probably okay.
      // maybe this can be done with Vuex?
      food: [
        'Schafskäse',
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
      orders: []
    };
  },
  mounted: function() {
    setInterval(() => {
      for (let index = 0; index < this.orders.length; index++) {
        const item = this.orders[index]
        this.orders[index].splice(2, 1, this.orders[index][2] - 1);
        if (this.orders[index][2] == 0) {
          this.$buefy.notification.open(
            `${item[0]} (x${item[1]}) ist jetzt fertig und abholbar!`
          );
          this.orders.splice(index, 1);
        }
      }
    }, 1000)
  },
  methods: {
    order(item, quantity) {
      const preparation_time = item.length * quantity
      this.orders.push([item, quantity, preparation_time])
    },
  }
}
</script>
