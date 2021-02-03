<template>
  <div>
    <b-navbar
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
      >
      <template #brand>
        <b-navbar-item tag="router-link" :to="{ path: '/' }">
          <img src="~/assets/logo.png" alt="Logo">
        </b-navbar-item>
      </template>
      <template #start>
        <b-navbar-item href="kontakt">
          Kontakt
        </b-navbar-item>
        <b-navbar-item href="historie">
          Historie
        </b-navbar-item>
      </template>
    </b-navbar>

    <div class="container column is-10">
      <nuxt />
    </div>

    <footer class="footer">
      <div class="content has-text-centered">
        <br><br>
        © Ledavi GROUP GmbH 2021
      </div>
    </footer>
  </div>
</template>

<style>
  body {
    background-color: #4158D0;
    background-image: linear-gradient(43deg, #4158D0 0%, #C850C0 46%, #FFCC70 100%);
  }
</style>

<script>
  export default {
    head () {
      return {
        title: 'Ledavi'
      }
    }
  }
</script>
