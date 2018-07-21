<template>
  <div class="add-dog">
        <app-navbar></app-navbar>
    <section class="flex">
      <div class="" align="center">
        <h1 class="the-h1" style="margin-top: 5%">Space Station</h1>
        <div class="intro"><p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dolores perspiciatis dolore sed hic aspernatur a nihil voluptatem inventore corrupti accusantium ratione, repellat labore quibusdam vitae tempora! Distinctio voluptatibus corporis nostrum?</p></div>
        <h2 class="subHeader">Dogs</h2>
      </div>

        <div class="container">
            <div class="wrapper">

                <ul class="dog" v-for="dog in dogs" :key="dog.first_name">
                    <li><img class="image" :src="dog.profile" alt="">
                    </li>
                    <li><p class="dogName">{{ dog.first_name }}</p></li>
                    <!-- <li><input type="number" placeholder="Amount"></li> -->
                    <div class="pay-button">
                        <li><button class="button2" type="submit" @click="tipDog(dog.id, 500)">Tip R5</button></li>
                        <li><button class="button2" type="submit" @click="tipDog(dog.id, 1000)">Tip R10</button></li>
                    </div>
                    <div class='figure' v-bind:style="{ 'animation-duration': calcDuration(dog)}"></div>
                </ul>

            </div>
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
                    // this.dogs = res.results;
                    for (const dog of res.results) {
                        dog.balance = 0;
                        this.dogs.push(dog);
                    }
                    return true;
                }, function (err) {
                    console.log('an error occured', err);
                }).then((res) => {
                    // Loop over each dog and get the balance
                    for (const dog of this.dogs) {
                        //https://api.rehive.com/3/admin/accounts/?user=3d80bc5d-dbe6-40d0-98d2-02a7de238e10
                        rehiveAdmin.admin.accounts.get({
                            filters: {
                                user: dog.id
                            }
                        }).then((res) => {
                            dog.balance = res.results[0].currencies[0].available_balance;
                            this.calcDuration(dog);
                        }, (err) => {
                            console.log('an error occured getting that dogs details', err);
                        });
                    }
                }, (err) => {
                    console.log('an error occured', err);
                });
            },
            tipDog: function(id, amount) {
                rehive.transactions.createTransfer(
                {
                    amount: amount,
                    recipient: id,
                    currency: "ZAR"
                }).then(function(res){
                    alert('tip succesful');
                    console.log('tip successful');
                },(err) => {
                    console.log('an error occured doing the transfer', err);
                    alert('An error occured');
                })
            },
            calcDuration(dog) {
                // Does the dog have a balance?
                if (!dog.balance) {
                    return `0.78s`;
                }
                // If we say R100 which is 10000cents is needed to walk a dog
                // We need to work out the % complete.
                const completePerc = dog.balance / 10000 * 100;

                // Upper limits 0.78s lower limits 0.4s
                // 1000 ms = 1s
                let animationTime = 1000 - (completePerc * 10);
                // Add in our lower animation limit incase funding is complete and the dog is executing at 0s
                animationTime = animationTime + 400;
                return `${animationTime}ms`;
            }
        },
        created() {
            this.getDogs();
            // this.tipDog();
        },
        components: {
          appNavbar:  navBar
        }
    }
</script>

<style>

.intro {
    padding: 1em;
}
.dogName{
  font-size: 1.8em;
  font-weight: 300;
}
.the-h1{
  font-weight: 300;
  font-size: 3em;
}

.image{
  height: 200px;
  width: 200px;
  border-radius: 50%;
}

.add-dog{
  min-height: 75vh;
}

.pay-button {
    display: flex;
    justify-content: center;
}

@media only screen and (max-width: 600px){
  .add-dog {
    overflow-x: hidden;
  }
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
    /* margin: 60px; */
    justify-items: center;
    text-align: center;
    grid-gap: 30px;
    margin: 2em;
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
    padding-left: 0px;
    padding: 1em;
    width: 100%;
    background-color: #f8f7f7;
    transition: all 300ms ease-in-out;
}

.dog:hover{
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

}

@media only screen and (max-width: 600px){
  .dog {
    background-color: #eff2f1;
    padding-top: 5px;
    padding-bottom: 5px;
  }
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
  padding: 10px 50px;
  /* border-radius: 10px; */
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
  /* height: 266px; */
  height: 360px;
  /* transform: translate3D(200px, 50px, 0); */
  transform: translate3D(50px, 50px, 0);
  /* the walking animation */
  animation: walk 0.78s steps(9) infinite;
  /* transform: translateZ(0); */
  backface-visibility: hidden;
}

@media only screen and (max-width: 600px){
  .figure{
    margin-right: 87px;
  }
}

    .no-svg .figure {
  background: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/57786/dog-walk.png");
}

@keyframes walk {
  100% { background-position: 0 -2376px; }
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
