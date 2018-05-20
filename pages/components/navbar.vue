<template lang="html">
  <div class="">
    <nav>
      <div class="handle" @click="show = !show"><i style="font-size:1.7em; color:white" class="fas fa-bars"></i></div>
      <ul v-bind:class="{showing: show}">
        <nuxt-link to="../organisation"><li>Organisations</li></nuxt-link>
        <nuxt-link to="../dogs"><li>Dogs</li></nuxt-link>
        <nuxt-link to="../dashboard"><li>Dashboard</li></nuxt-link>
      </ul>
    </nav>
  </div>

</template>

<script>
export default {
  data: function() {
    return {
      show: false
    }
  }
}
</script>

<style lang="css">

nav ul{
  background: #80CBC4;
  overflow: hidden;
  padding: 0;
  text-align: center;
  margin: 0;
  -webkit-transition: max-height 0.4s;
  -ms-transition: max-height 0.4s;
  -moz-transition: max-height 0.4s;
  -o-transition: max-height 0.4s;
  transition: max-height 0.4s;
}

nav ul li{
  display: inline-block;
  padding: 20px;
  color: white;
  border-bottom: none;
}

nav ul li:hover{
  background: #68adad;
}

.handle{
  width: 100%;
  background: #80CBC4;
  text-align: left;
  box-sizing: border-box;
  padding: 15px 10px;
  cursor: pointer;
  display: none;
}

@media screen and (max-width: 580px){
 nav ul{
   max-height: 0;
 }
.showing{
   max-height: 20em;
 }
 nav ul li{
    box-sizing: border-box;
    width: 100%;
    padding: 15px;
    text-align: left;
  }

  .handle{
    display: block;
  }
}
</style>
