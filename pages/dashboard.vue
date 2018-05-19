<template>
  <section class="dashboard">
    <div class="header" align="center">
        <div class="title">
          <h1 class="the-h1">Organisations</h1>
        </div>

    </div>

      <div class="container">
          <div class="wrapper">

              <ul class="dog" v-for="group in groups" :key="group.name">
                  <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  <li><p>{{group.name}}</p></li>
                  <li><p>{{group.description}}</p></li>
                  <li>  <nuxt-link to="/dogs"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
              </ul>
              
          </div>
      </div>

      <div class="logo-div" align="right">
        <img src="../assets/logo2.png" alt="" class="logo">
      </div>
  </section>
</template>

<script>

import Rehive from 'rehive';

const rehive = new Rehive({storageMethod: 'local'});
const rehiveAdmin = new Rehive({apiToken: '5118a45f37886966747bec5e385c4884364f277de77a30de2da31b93f3f2a3e8'});

export default {
  data: function(){
    return {
      groups: [],
    }
  },
  methods: {
    getGroups: function() {
      rehiveAdmin.admin.groups.get().then((res) => {
        // Get all the groups, ignore user, service and admin
        const blackListGroups = ['user', 'service', 'admin'];
        for (const group of res.results) {
          // If the group is not blacklisted
          if (!blackListGroups.includes(group.name)) {
            this.groups.push(group);
          }
        }
      }, (err) => {
        console.log('Oh no an error occured when getting the groups', err);
        alert('Oh no an error occured when getting the groups');
      });
    },
    getRoute(name) {
      return `/organisation/${name}`;
    }
  },
  created() {
    this.getGroups();
  }
}
</script>

<style>

body{
  font-family: sans-serif;
}

.logo{
  height: 70px;
  width: 70px;
  margin-right: 1%;
}

.logo-div{
  margin-left: 1%;
}

.header-flex{
  display: flex;
  justify-content: flex-start;
  width: 100%;
}

.container {
    width: 100%;
    min-height: 70vh;
}

.flex {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: auto;
}

.wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    margin: 60px;
    justify-items: center;
    text-align: center;
    grid-gap: 10px;
}

ul li {
    padding: 10px;
    list-style: none;
}


.dog img {
    height: 170px;
}

.header{
  font-family: sans-serif;
  font-weight: 100;
  font-size: 2.0em;
  margin-top: 20px;
}

.subHeader {
    font-family: sans-serif;
    font-weight: 100;
    font-size: 2em;
    margin-top: 20px;
}

.button2 {
  /* position: relative; */
  padding: 10px 10px;
  border-radius: 10px;
  font-family: sans-serif;
  font-size: 1.0em;
  color: #FFF;
  text-decoration: none;
  border: 0;
  background-color: #80CBC4;
  cursor: pointer;
}

.button2:hover {
  background-color: #4f9a94;
}

.the-h1{
  font-weight: 100;
  font-size: 1.5em;
}

.header{
  grid-area: header;
  width: 100%;
  display: flex;
}


.title {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.button {
  /* position: relative; */
  padding: 10px 10px;
  border-radius: 10px;
  font-family: sans-serif;
  font-size: 1.0em;
  color: #FFF;
  text-decoration: none;
  border: 0;
  background-color: #80CBC4;
  cursor: pointer;
}

.button:hover {
  background-color: #4f9a94;
}

</style>
