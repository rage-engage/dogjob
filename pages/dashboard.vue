<template>
  <section class="dashboard">
    <div class="header" align="center">
        <div class="title">
          <h1 class="the-h1">Organisations</h1>
        </div>

    </div>

      <div class="container">
          <div class="wrapper">
              <ul class="dog">
                  <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  <li><p>Space Station</p></li>
                  <li><p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis</p></li>
                  <li>  <nuxt-link to="/add-dog"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
              </ul>

              <ul class="dog">
                  <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  <li><p>Space Station</p></li>
                  <li><p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis</p></li>
                  <li>  <nuxt-link to="/add-dog"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
              </ul>

              <ul class="dog">
                  <li><img class="image" src="../assets/Ss.jpg" alt=""></li>
                  <li><p>Space Station</p></li>
                  <li><p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis</p></li>
                  <li>  <nuxt-link to="/add-dog"> <button class="button" type="submit">View Dogs</button> </nuxt-link></li>
              </ul>
          </div>
      </div>

      <div class="logo-div" align="right">
        <img src="../assets/logo2.png" alt="" class="logo">
      </div>
  </section>
</template>

<script>
export default {

}
</script>

<style>

body{
  font-family: sans-serif;
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


.dog img {
    height: 170px;
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
