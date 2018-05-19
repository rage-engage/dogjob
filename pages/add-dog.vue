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
                    <li><p>Description: Dog is a good boy</p></li>
                    <li><p>Breed: Dog</p></li>
                    <li><input type="number" placeholder="Amount"></li>
                    <li><button class="button2" type="submit">Submit</button></li>
                    <div id="myProgress">
                      <div id="myBar"></div>
                    </div>
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

const rehive = new Rehive({storageMethod: 'local'});



export default {

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

</style>
