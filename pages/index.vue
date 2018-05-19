<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        dogjob
      </h1>
      <h2 class="subtitle">
        Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green">Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey">GitHub</a>
      </div>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import rehive from 'rehive';

export default {
  components: {
    AppLogo
  },
  methods: {
    login: function() {
      console.log('rehive is', rehive);
      rehive.auth.login({
          user: "dracogio@gmail.com",
          company: "dogjob",
          password: "password"
      }).then(function(user){
          console.log('user is', user);
      },function(err){
          console.log('oh no something went wrong');
      })
    }
  },
  created: function(){
      console.log('hejj');
      this.login();
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
