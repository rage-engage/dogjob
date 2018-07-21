<template>
  <section class="dashboard">
    <app-navbar></app-navbar>
    <div class="header" align="center">
        <div class="title">
          <h1 class="the-h1">Organisations</h1>
        </div>
    </div>
    <div class="paragraph">
      <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquam autem vel quo sed assumenda quod a ipsam mollitia et. At, similique doloremque minus repudiandae quis aspernatur officiis sequi vitae maiores? Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquam autem vel quo sed assumenda quod a ipsam mollitia et. At, similique doloremque minus repudiandae quis aspernatur officiis sequi vitae maiores?</p>
    </div>

      <div class="container">
          <div class="wrapper">
              <ul class="dog" v-for="group in groups" :key="group.name">
                  <div class="dog-image">
                    <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  </div>
                  <div class="dog-org-info">
                    <li><p>{{group.name}}</p></li>
                    <li><p>{{group.description}}</p></li>
                    <li>  <nuxt-link to="/dogs"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
                  </div>
              </ul>
          </div>
            <div class="wrapper">
              <ul class="dog" v-for="group in groups" :key="group.name">
                  <div class="dog-image">
                    <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  </div>
                  <div class="dog-org-info">
                    <li><p>{{group.name}}</p></li>
                    <li><p>{{group.description}}</p></li>
                    <li>  <nuxt-link to="/dogs"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
                  </div>
              </ul>
          </div>
      </div>
      <!-- Footer -->
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
  },
  components: {
    appNavbar:  navBar
  }
}
</script>

<style>
@media only screen and (max-width: 600px){
  .dashboard {
    overflow-x: hidden;
  }
}

body{
  font-family: sans-serif;
}

.paragraph {
  display: flex;
  justify-content: center;
  padding: 2em;

}

.image{
  height: 200px;
  /* width: 200px; */
  border-radius: 50%;
  padding: 0.5em;
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
    padding-top: 2em;
    margin-bottom: 3em;
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
    /* margin: 60px; */
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

.dog {
  padding: 0em;
  display: flex;
  align-items: center;
  width: 90%;
  margin: 1em;
  background-color: #f8f7f7;
  transition: all 300ms ease-in-out;
}

.dog:hover {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.dog-org-info {
  width: 50%;
}

ul li {
    padding: 10px;
    list-style: none;
}
@media only screen and (max-width: 600px){
  ul {
    padding-left: 0;
  }
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
  /* border-radius: 10px; */
  font-family: sans-serif;
  font-size: 1.0em;
  color: #FFF;
  text-decoration: none;
  border: 0;
  background-color: #80CBC4;
  cursor: pointer;
  width: 100%;
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
  margin-top: -1px;
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
