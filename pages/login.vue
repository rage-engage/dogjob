<template>
  <div class="">
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
  </div>
</template>

<script>
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
  }
}

</script>

<style>
.flex {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
}

.header{
  font-family: sans-serif;
  font-weight: 400;
  font-size: 2.0em;
}

.form {
  width: 30%;
  height: auto;
  background-color: white;
  margin: 3% auto 100px;
  padding: 45px;
  border-radius: 5%;
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

.link{
  font-size: 15px;
  color: #79c4bd;

}

.error{
  margin-top: 5%;
  background: FIREBRICK;
  color: WHITE;
  padding: 10px;
  border-radius: 3px;
}
</style>
