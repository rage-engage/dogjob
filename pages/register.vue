<template>
  <section class="flex">
    <h1 class="header">Register page</h1>
      <div class="form">
        <form class="" action="index.html" method="post">
          <label for="">First Name</label>
          <input class="input" type="text" name="" id="firstName">
          <label for="">Last Name</label>
          <input class="input" type="text" name="" id="lastName">
          <label for="">E-mail Address</label>
          <input class="input" type="text" name="" id="email">
          <label for="">Password</label>
          <input class="input" type="text" name="" id="password">
          <button class="button" type="button" name="button">Register</button>
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
