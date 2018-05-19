<template>
  <section class="container">
    <div>
      <img src="../assets/logo.png" alt="" class="test">
      <!-- <h1 class="title">
        Dog Jog
      </h1> -->
      <h2 class="subtitle">
        Help dog shelters walk their dogs
      </h2>
      <div class="links">
        <nuxt-link to="./login" class="button--green">Login</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {

}
</script>

<style>
.test{
  height: 400px;
  width: 400px;
}
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
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 30px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
