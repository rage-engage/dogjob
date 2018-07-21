<template>
  <div class="">
    <app-navbar></app-navbar>
    <section class="flex">
      <h1 class="header">Register page</h1>
        <div class="form">
          <form class="" action="index.html" method="post">
            <label for="">First Name</label>
            <input class="input" v-model="first_name" type="text" name="" id="firstName" required>
            <label for="">Last Name</label>
            <input class="input" v-model="last_name" type="text" name="" id="lastName" required>
            <label for="">E-mail Address</label>
            <input class="input" v-model="email" type="text" name="" id="email" required>
            <label for="">Password</label>
            <input class="input" v-model="password1" type="text" name="" id="password" placeholder="Password must have at least 8 charachters" required>
            <label for="">Confirm Password</label>
            <input class="input" v-model="password2" type="text" name="" id="password" placeholder="Password must have at least 8 charachters" required>
            <button class="button" type="button" name="button" @click="register">Register</button>
          </form>
        </div>
    </section>
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
  </div>
</template>

<script>
import navBar from './components/navbar'
import Rehive from 'rehive';

const rehive = new Rehive({storageMethod: 'local'});



export default {
  data: function() {
    return {
      first_name: '',
      last_name: '',
      email: '',
      password1: '',
      password2: '',
    }
  },
  methods: {
    register: function() {
      console.log('rehive is', rehive);
      rehive.auth.register({
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        password1: this.password1,
        password2: this.password2,
        company: 'dogjob'
      }).then(function(user){
          console.log('user is', user);
      },function(err){
          console.log('oh no something went wrong', err);
      })
    }
  },
  components: {
  appNavbar:  navBar
}
}

</script>

<style>

#password {
  font-size: 12px;
}

.flex {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: auto;
  padding: 4em 4em 2em;
}

.header{
  font-family: sans-serif;
  font-weight: 300;
  font-size: 2.0em;
}

.form {
  width: 30%;
  height: auto;
  background-color: white;
  /* margin: 3% auto 100px; */
  padding: 45px;
  border-radius: 5%;
  /* box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.1), 0 5px 5px 0 rgba(0, 0, 0, 0.1); */
}

.input {
  width: 100%;
  font-size: 15px;
  margin: 0 0 15px;
  border: none;
  border-bottom: 1px solid #7f8184;
  padding-bottom: 7px;
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
