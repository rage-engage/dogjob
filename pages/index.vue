<template>
<div>
  <section class="container">
    <div class="left-wrapper">
      <div class="welcome">
        <h1>Welcome, to DogJog</h1>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Dolorum, ipsa!</p>
      </div>
      <div class="icon-wrapper">
        <div class="icon">
          <i class="fas fa-money-bill-alt fa-5x"></i>
          <p>Easy Payments</p>
        </div>
        <div class="icon">
          <i class="fas fa-briefcase fa-5x"></i>
          <p>Job Creation</p>
        </div>
        <div class="icon">
          <i class="fas fa-life-ring fa-5x"></i>
          <p>Supports the Shelter</p>
        </div>
        <div class="icon">
          <i class="fas fa-heart fa-5x"></i>
          <p>Love to Dogs</p>
        </div>
      </div>
    </div>
    <div>
      <img src="../assets/logo.png" alt="" class="test">
      <div class="links">
        <nuxt-link to="./login" class="button--green">Login</nuxt-link>
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
export default {

}
</script>

<style>
.welcome {
  margin-bottom: 2em;
}

.welcome h1 {
  font-size: 2em;
  font-weight: 300;
  margin-bottom: 0.5em;
}
.test{
  height: 400px;
  width: 400px;
}

@media only screen and (max-width: 600px){
  .test {
    width: 100%;
    height: auto;
  }
}
.container {
  /* min-height: 100vh; */
  display: flex;
  /* flex-direction: column; */
  justify-content: space-around;
  align-items: center;
  text-align: center;
  margin-bottom: 3em;
  margin-top: 2em;
}

.icon-wrapper {
  display: flex;
  justify-content: center;
}

.icon {
  padding: 1em;
}

.icon i {
  padding: 0.5px;
  color: #4f9a94;
}

.icon p {
  font-size: 12px;
  margin-top: 1rem;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 30px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.button--green {
  width: 70%;
  border-radius: 0px;
  transition: all 400ms ease-in-out;
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
