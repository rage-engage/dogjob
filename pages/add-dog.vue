<template>
  <div class="">

    <app-navbar></app-navbar>
    <section class="flex">
      <h1 class="header">Add Dog</h1>
        <div class="form">
          <form class="" action="index.html" method="post">
            <label for="">Name</label>
            <input type="text" name="" value="" class="input" v-model="name" v-modal="name">
            <div class="" align="center">
              <button class="button" type="button" name="button" @click="addDog">Submit</button>
              <!-- <p class="error" v-if="error.status"> {{ error.msg }}</p> -->
            </div>

          </form>
        </div>
    </section>
  </div>

</template>

<script>
import navBar from './components/navbar'
import Rehive from 'rehive';

const rehiveAdmin = new Rehive({apiToken: '5118a45f37886966747bec5e385c4884364f277de77a30de2da31b93f3f2a3e8'});

export default {
  data: function(){
    return {
      name: ''
    }
  },
  methods: {
    addDog() {
      let formData = new FormData;
      rehiveAdmin.admin.users.create({'first_name': this.name, 'metadata': {'type': 'dog'}}).then((res) => {
        console.log('res is ', res)
      }, (err) => {
        console.log('An error occured while adding a dog', err);
        alert('Could not add a dog');
      });
    }
  },
  components: {
    appNavbar:  navBar
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
  font-weight: 300;
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
</style>
