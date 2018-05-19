<template>
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
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
                <ul class="dog">
                  <li><img src="../assets/DogJog.png" alt=""></li>
                  <li><p>Dog Name: Name</p></li>
                  <li><p>Description: Dog is a good boy</p></li>
                  <li><p>Breed: Dog</p></li>
                  <label for="">Tip Amount:</label>
                  <li><input type="number"></li>
                  <li><button class="button" type="submit">Submit</button></li>
              </ul>
              
          </div>
      </div>

  </section>
</template>

<script>
import Rehive from 'rehive';

const rehive = new Rehive({storageMethod: 'local'});



export default {

}

</script>

<style>

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
  font-weight: 400;
  font-size: 2.0em;
  margin-top: 20px;
}

.subHeader {
    font-family: sans-serif;
    font-weight: 100;
    font-size: 1.5em;
    margin-top: 20px;
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

input { 
    text-align: center;
    border: none;
    border-bottom: 1px solid black;
}

</style>
