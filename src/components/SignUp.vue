<template>
  <h2>Sign Up Here</h2>
  <div class="register">
    <input type="text" v-model="fname" placeholder="Enter First Name:" />
    <input type="text" v-model="lname" placeholder="Enter Last Name:" />
    <input type="text" v-model="email" placeholder="Email:" />
    <input type="password" v-model="password" placeholder="Password:" />
    <button v-on:click="signUp" class="signup">Sign Up</button>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'SignUp',
  data() {
    return {
      fname: '',
      lname: '',
      email: '',
      password: '',
    };
  },
  methods: {
    async signUp() {
      console.warn(
        'signUp method is Working Fine',
        this.fname,
        this.lname,
        this.email,
        this.password,
      );
      let result = await axios.post('http://localhost:3000/user', {
        fname: this.fname,
        lname: this.lname,
        email: this.email,
        password: this.password,
      });
      console.warn(result);
      if (result.status == 201) {
        alert('Sign Up is completed.');
        alert('Success');
      }
    },
  },
};
</script>
<style>
.register input {
  height: 30px;
  width: 300px;
  padding-left: 10px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 30px;
}
.register button {
  height: 30px;
  width: 320px;
  padding-left: 10px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 30px;
  color: white;
  background-color: black;
}
</style>
