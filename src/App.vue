<template>
  <div id="app" class="container">
    <section>
      <h1>Pay with Bitnob</h1>
      <div class="form-container">
        <hr />
        <div>
          <div class="input-div">
            <label for="email"><b>Email</b></label>
            <input
              type="text"
              placeholder="Enter Email"
              name="email"
              id="email"
              required
            />
          </div>
          <div class="input-div">
            <label for="amount"><b>Amount</b></label>
            <input
              type="number"
              placeholder="Enter amount in Naira"
              name="amount"
              id="amount"
              required
            />
          </div>
          <bitnob
            :amount="amount"
            :currency="currency"
            :customerEmail="email"
            :publicKey="publicKey"
            :reference="reference"
            :environment="environment"
            :notificationEmail="notificationEmail"
          >
            Make Payment
          </bitnob>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import Vue from "vue";


import { Bitnob } from "vue-bitnob";

export default Vue.extend({
  name: "App",
  components: {
    Bitnob,
  },
  data() {
    return {
      publicKey: "pk.9058f.0a5cb70de0f5853b9febfa",
      email: "foobar@example.com",
      amount: 10000,
      currency: "NGN",
      notificationEmail: "gabbyprecious2000@gmail.com",
      environment: "sandbox",
    };
  },
  computed: {
    reference() {
      let text = "";
      let possible =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

      for (let i = 0; i < 10; i++)
        text += possible.charAt(Math.floor(Math.random() * possible.length));

      return text;
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  overflow-x: hidden;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Quicksand", sans-serif;
}

.container {
  padding: 3rem;
  display: flex;
  align-items: center;
  flex-direction: column;
  /* height: 100%;
            width: 100%; */
}

.form-container {
  display: flex;
  flex-direction: column;
  width: 400px;
}

.form-container div {
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
}

.form-container input {
  border: 1px solid black;
  border-radius: 5px;
  padding: 15px;
  margin-bottom: 10px;
  width: 75%;
}

.input-div {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.button-div {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

input {
  box-sizing: border-box;

  background: #ffffff;
  border: 1px solid rgba(153, 163, 160, 0.6);
  border-radius: 16px;
}

p {
  font-size: 14px;
  font-weight: 900;
}
</style>
