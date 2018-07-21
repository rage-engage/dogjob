<template>
  <div class="">
    <app-navbar></app-navbar>
    <section class="flex">
      <h1 class="header">Login</h1>
        <div class="form">
          <form class="" action="index.html" method="post">
            <label for="">Email</label>
            <input type="text" name="" value="" class="input" v-model="email">
            <label for="">Password</label>
            <input type="password" name="" value=""  class="input" v-model="password">
            <div class="" align="center">
              <button class="button" type="button" name="button" @click="login">Submit</button>
              <br><br>
              <nuxt-link to="/register" class="link">Not a member? Sign up</nuxt-link>

              <p class="error" v-if="error.status"> {{ error.msg }}</p>
            </div>

          </form>
        </div>
    </section>
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
  data: function(){
    return {
      email: '',
      password: '',
      error: {
        status: false,
        msg: "invalid login"
      }
    }
  },
  methods: {
    login: function() {
      rehive.auth.login({
          user: this.email,
          company: "dogjob",
          password: this.password
      }).then((user) => {
          this.$router.push({ path: `/dashboard` });
      },(err) =>{
          console.log('oh no something went wrong',err);
          this.error.status = true;
          this.error.msg = "Invalid login";
      })
    }
  },
  components: {
  appNavbar:  navBar
}
}

</script>

<style scoped>

</style>

<style>
.flex {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: auto;
  padding: 4em;
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
}

@media only screen and (max-width: 600px){
  .form {
    padding-left: 0;
    padding-right: 0;
    width: 80%;
  }
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
  width: 100%;
  padding: 10px 10px;
  /* border-radius: 10px; */
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

.link{
  font-size: 15px;
  color: #79c4bd;

}

.error{
  margin-top: 5%;
  background: #f28585;
  color: WHITE;
  padding: 10px;
  border-radius: 3px;
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
