<script >
export default {
  data() {
    return {
      accountButtonText: 'Login',
      loggedIn: false
    }
  },
  methods: {
    submitForm() {
      this.accountButtonText = "Logout";
      this.loggedIn = true;
    },
    logout() {
      this.accountButtonText = "Login";
      this.loggedIn = false;
    }
  }
}
</script>

<template>

  <header>
    <div class="navigation">
      <a v-if="!loggedIn" href="#" class="button button-secondary">{{ accountButtonText }}</a>
      <button v-if="loggedIn" v-on:click="logout()" type="button" class="button button-secondary">{{ accountButtonText }}</button>
    </div>
  </header>

  <section>
    <div class="form-container" v-if="!loggedIn">
      <h1>Login</h1>
      <form class="loginForm" v-on:submit.prevent="submitForm()" action="">
        <div class="form-row">
          <label for="email">E-mail</label>
          <input type="email" name="email" id="email">
        </div>
        <div class="form-row">
          <label for="password">Wachtwoord</label>
          <input type="password" name="password" id="password">
        </div>
        <div class="form-action">
          <button class="button button-primary" type="submit">{{ accountButtonText }}</button>
        </div>
      </form>
    </div>
    <div class="container" v-else>
      <h1>Welkom!</h1>
      <p>Je bent succesvol ingelogd!</p>
      <button v-on:click="logout()" type="button" class="button button-secondary">{{ accountButtonText }}</button>
    </div>
  </section>

</template>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

header {
  width: 100%;
  display: flex;
  justify-content: end;
  background-color: #C7CCB9;
}

.navigation {
  margin: 1rem;
}

.container {
  text-align: center;
}

.button {
  position: relative;
  display: inline-block;
  appearance: none;
  -webkit-appearance: none;
  margin: 0;
  width: auto;
  overflow: visible;
  cursor: pointer;

  padding: .3rem .6rem;

  background-color: transparent;
  border-radius: 5px;
  border: 0;
  color: white;
  text-align: center;
  text-decoration: none;
  text-shadow: none;

  transition: background-color 0.1s, border-color 0.1s, color 0.1s, box-shadow 0.1s, outline 0.1s;
}

.button-secondary {
  background-color: #DBF9B8;
  color: #0F0F0F;
}

.button-secondary:hover {
  background-color: #87A878;
  color: #EBEBEB;
}

.button-primary {
  background-color: #87A878;
  color: #EBEBEB;
}

.button-primary:hover {
  background-color: #DBF9B8;
  color: #0F0F0F;
}

section {
  width: 50%;
  margin: 5rem auto;
}

.loginForm {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

.form-row {
  width: 100%;
  margin: .5rem .2rem;
}

label {
  display: block;
  width: 100%;
}
input {
  width: 100%;
}

.form-action {
  width: 100%;
  margin: 1rem 0;
  display: flex;
  justify-content: center;
}

</style>
