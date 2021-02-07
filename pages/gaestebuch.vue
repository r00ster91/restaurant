<template>
<section>
  <section class="hero">
    <div class="hero-body">
      <p class="title has-text-centered">
        Wie war Ihr Aufenthalt? Haben Sie Feedback oder Anregungen?
        <br />
        Wir freuen uns auf Ihre Nachricht.
      </p>
    </div>
  </section>

  <b-field label="Name">
    <b-input v-model="name" maxlength="35" />
  </b-field>
  <b-field label="E-Mail (optional für Rückfragen)">
    <b-input v-model="email" maxlength="35" />
  </b-field>
  <b-field label="Ihre Nachricht">
    <b-input v-model="message" maxlength="500" type="textarea" />
  </b-field>
  <b-button @click="submit">Absenden</b-button>

  <div v-for="(entry, index) of guestbook" :key="index" class="container">
    <br />
    <div class="notification is-primary" style="
          background-image: linear-gradient(#c850c0 46%, #4158d0 100%);
          border: 3px solid #ffcc70;
        ">
      <strong>{{ entry[0] }}</strong> schrieb:
      <br />
      {{ entry[1] }}
      <div v-if="admin == true">
        <br />
        <strong>E-Mail: </strong>{{ entry[2] }}
        <br />
        <b-button @click="edit_entry(index)">Bearbeiten</b-button>
        <b-button @click="delete_entry(index)" type="is-danger">Löschen</b-button>
      </div>
    </div>
  </div>

  <br /><br />
  <b-button @click="log_in_or_out" type="is-dark">
    <div v-if="admin == false">Adminbereich</div>
    <div v-else>Ausloggen</div>
  </b-button>
</section>
</template>

<script>
'use strict';

export default {
  data() {
    return {
      name: '',
      message: '',
      email: '',
      guestbook: [],
      admin: false,
    };
  },
  beforeMount() {
    const item = window.localStorage.getItem('guestbook');
    if (item) {
      this.guestbook = JSON.parse(item);
    }
  },
  methods: {
    update_storage() {
      const json = JSON.stringify(this.guestbook);
      try {
        localStorage.setItem('guestbook', json);
      } catch {
        this.$buefy.notification.open(
          'Entschuldigung, da ist etwas schiefgelaufen.'
        );
        return false;
      }
      return true;
    },
    edit_entry(index) {
      let input;
      input = prompt('Neuer Name (freilassen zum Ignorieren):');
      if (input != '') {
        this.guestbook[index].splice(0, 1, input);
      }
      input = prompt('Neue Nachricht (freilassen zum Ignorieren):');
      if (input != '') {
        this.guestbook[index].splice(1, 1, input);
      }
      this.update_storage();
    },
    delete_entry(index) {
      if (confirm('Sind Sie sicher?')) {
        if (index > -1) {
          this.guestbook.splice(index, 1);
        }
        this.update_storage();
      }
    },
    log_in_or_out() {
      if (this.admin == true) {
        this.admin = false;
        this.$buefy.notification.open('Erfolgreich ausgeloggt.');
      } else {
        const input = prompt('Passwort:');

        // NOTE: everyone can read this password from the source code.
        //       Not suitable for a real world use case
        if (input == 'leonardo') {
          this.admin = true;
          this.$buefy.notification.open('Willkommen!');
        } else {
          this.$buefy.notification.open('Das hat leider nicht geklappt.');
        }
      }
    },
    submit() {
      let name = this.name;
      if (name == '') {
        name = 'Unbekannter Nutzer';
      }

      let email = this.email;
      if (email == '') {
        email = 'E-Mail nicht angegeben';
      }

      this.guestbook.push([name, this.message, email]);

      if (this.update_storage()) {
        this.$buefy.notification.open(
          'Vielen Dank. Ihre Nachricht wurde erfolgreich gespeichert.'
        );
      }
    },
  },
};
</script>
