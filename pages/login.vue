<template>
  <section class="flex">
    <h1 class="header">Login</h1>
      <div class="form">
        <form class="" action="index.html" method="post">
          <label for="">Username</label>
          <input type="text" name="" value="" class="input">
          <label for="">Password</label>
          <input type="password" name="" value=""  class="input">
          <div class="" align="center">
            <button class="button" type="button" name="button">Submit</button>
          </div>

        </form>
      </div>
  </section>
</template>

<script>

export default {

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
