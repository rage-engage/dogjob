<template>
  <section class="dashboard">
      <app-navbar></app-navbar>
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
      <footer>
        <div class="footer-image"></div>
          <div class="footer-wrapper">
            <div class="footer-logo-wrapper"><img src="../../dogjob/assets/logo2.png" alt=""></div>
            <div class="footer-text-blocks">
              <div>
                <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Natus doloremque repellat harum! Saepe porro distinctio exercitationem veritatis, delectus, accusantium quasi natus totam nostrum tempore repellat labore repellendus rem ad consequatur!</p>
              </div>
              <div>
                <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Natus doloremque repellat harum! Saepe porro distinctio exercitationem veritatis, delectus, accusantium quasi natus totam nostrum tempore repellat labore repellendus rem ad consequatur!</p>
              </div>
              <div>
                <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Natus doloremque repellat harum! Saepe porro distinctio exercitationem veritatis, delectus, accusantium quasi natus totam nostrum tempore repellat labore repellendus rem ad consequatur!</p>
              </div> 
          </div>
        </div>
    </footer>
  </section>
</template>

<script>
import navBar from './components/navbar'
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
    },
    components: {
      appNavbar:  navBar
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

.dog {
  padding: 1em;
  background-color: #eff2f1;
  width: 100%;
  transition: all 300ms ease-in-out;
}

.dog:hover{
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

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
    margin: 2em;
    justify-items: center;
    text-align: center;
    grid-gap: 30px;
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
    height: 200px;
    border-radius: 50%;
}

.header{
  font-family: sans-serif;
  font-weight: 100;
  font-size: 2.0em;
  margin-top: 20px;
}
@media only screen and (max-width: 600px){
  .header {
    font-size: 1em;
  }
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
  /* border-radius: 10px; */
  font-family: sans-serif;
  font-size: 1.0em;
  color: #FFF;
  text-decoration: none;
  border: 0;
  background-color: #80CBC4;
  cursor: pointer;
  width: 20%;
  transition: all 400ms ease-in-out;
}

.button:hover {
  background-color: #4f9a94;
}

/* Footer */
.footer-image {
  background-image: url("../../dogjob/assets/Rectangle_2.png");
  background-repeat: no-repeat;
  height: 5.8rem;
  display: flex;
  justify-content: center;
}

.footer-logo-wrapper {
  align-self: center;
}

.footer-wrapper img {
  width: 50px;
  align-self: center;
}

.footer-wrapper {
  display: flex;
  flex-direction: column;
  align-self: center;
  background: #80CBC4;
  width: 100%;
  height: auto;
  margin-top: -2px;
}

.footer-text-blocks {
  display: flex;
  justify-content: center;
  align-self: center;
  width: 90%;
  margin-top: 1em;
}

.footer-text-blocks p {
  padding: 1em;
  color: white;
  margin-bottom: 2em;
}

</style>
