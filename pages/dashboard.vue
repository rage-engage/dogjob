<template>
  <section class="dashboard">
    <div class="header" align="center">
        <div class="title">
          <h1 class="the-h1">Welcome, Space Station</h1>
        </div>

    </div>
    <div class="" align="center" style="margin-top: 3%;">
      <nuxt-link to="./add-dog"><button class="button"> <i class="fas fa-plus"></i> Add dog</button></nuxt-link>
    </div>

      <div class="container">
          <div class="wrapper">
              <ul class="dog" v-for="dog in dogs" :key="dog.first_name">
                  <li><img class="image" :src="dog.profile" alt=""></li>
                  <li><p>{{dog.first_name}}</p></li>
                  <li>
                    <nuxt-link to="./edit-dog"><button class="button" type="submit" style="background-color: #8cd162; margin-right: 7%"><i class="fas fa-pencil-alt"></i></button></nuxt-link>
                    <button class="button" type="submit" style="background-color: #d16262"><i class="fas fa-trash-alt"></i></button>
                    </li>
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
    data: function() {
        return {
            dogs: [],
        }
    },
    methods: {
        getDogs: function() {
            rehiveAdmin.admin.users.get({
                filters: {
                    metadata__type: 'dog'
                }
            }).then((res) => {
                this.dogs = res.results;
                console.log('res is', res);
            }, function (err) {
                console.log('an error occured', err);
            });
        },
        tipDog: function() {
            rehive.transactions.createTransfer(
            {
                amount: 100,
                recipient: "7660da2d-097a-410a-9089-bfbf72629fd9",
                currency: "ZAR"
            }).then(function(res){
                console.log('tip successful');
            },(err) => {
                console.log('an error occured doing the transfer', err);
                alert('An error occured');
            })
        }
    },
    created() {
        console.log('hello');
        this.getDogs();
        // this.tipDog();
    }
}
</script>

<style>

body{
  font-family: sans-serif;
}


.image{
  height: 200px;
  width: 200px;
  border-radius: 50%;
}

.logo{
  height: 70px;
  width: 70px;
  margin-right: 1%;
}

.logo-div{
  margin-left: 1%;
}
.dog{
  padding: 0;
  background-color: #eff2f1;
  border-radius: 5%;
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
    margin: 60px 130px;
    justify-items: center;
    text-align: center;
    grid-gap: 10px;
}

@media only screen and (max-width: 600px){
  .wrapper {
    margin-left: 0;
    margin-right: 0;
  }
}

ul li {
    padding: 10px;
    list-style: none;
}

.dog {
  background-color: #efefef;
}

.dog img {
    height: 170px;
    border-radius: 50%;
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
