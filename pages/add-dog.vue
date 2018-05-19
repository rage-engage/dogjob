<template>
  <div class="add-dog">
    <section class="flex">
        <h1 class="mainHeader">Space Station</h1>
        <h2 class="subHeader">Dogs</h2>
        <div class="container">
            <div class="wrapper">
                <ul class="dog">
                    <li><img class="image" src="../assets/DogJog.png" alt=""></li>
                    <li><p>Dog Name: Name</p></li>
                    <!-- <li><p>Description: Dog is a good boy</p></li>
                    <li><p>Breed: Dog</p></li> -->
                    <li><input type="number" placeholder="Amount"></li>
                    <li><button class="button2" type="submit" @click="addDog()">Submit</button></li>

                    <div class='figure'></div>
                    <!-- <div id="myProgress">
                      <div id="myBar"></div>
                    </div> -->
                </ul>

            </div>
        </div>
    </section>
    <div class="logo-div" align="right">
      <img src="../assets/logo2.png" alt="" class="logo">
    </div>
  </div>

</template>

<script>
import Rehive from 'rehive';

const rehiveAdmin = new Rehive({apiToken: '5118a45f37886966747bec5e385c4884364f277de77a30de2da31b93f3f2a3e8'});

export default {
  data: function(){
    return {
      progress: 0
    }
  },
  methods: {
    addDog() {
      let formData = new FormData;
      rehiveAdmin.admin.users.create({'first_name': 'woof', 'metadata': {'type': 'dog'}}).then((res) => {
        console.log('res is ', res)
      }, (err) => {
        console.log('An error occured while adding a dog', err);
        alert('Could not add a dog');
      });
    }
  }

}

</script>

<style>

.add-dog{
  min-height: 75vh;
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
    height: auto;
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

.dog {
    padding-left: 0px;
}

.dog img {
    height: 170px;
}

.mainHeader{
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

#myProgress {
    width: 100%;
    background-color: grey;
}
#myBar {
    width: 30%;
    height: 15px;
    background-color: #80CBC4;
}

/* dog walking */
.figure {
  background: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/57786/dog-walk.svg") no-repeat;
  width: 220px;
  height: 266px;
  transform: translate3D(200px, 50px, 0);
  /* the walking animation */
  animation: walk 0.78s steps(9) infinite;
  transform: translateZ(0);
  backface-visibility: hidden;
}
.no-svg .figure {
  background: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/57786/dog-walk.png");
}

@keyframes walk {
  100% { background-position: 0 -2376px; }
}
</style>
