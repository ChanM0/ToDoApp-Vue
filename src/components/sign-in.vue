<template>
  <form>
    <div class="form-group">
      <label for="email">Email</label>
      <input 
        type="email"
        id="email"
        name="email"
        class="form-control"
        v-model="email">
      <label for="password">Password</label>
      <input 
        type="password"
        id="password"
        name="password"
        class="form-control"
        v-model="password">
    </div>
    <button type="submit" class="btn btn-primary" @click.prevent="signIn" >Sign In</button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    signIn() {
      var path =
        "http://localhost:8888/ApplicationCreation/ToDoApp/public/api/user/signIn";
      axios
        .post(
          path,
          {
            email: this.email,
            password: this.password
          },
          {
            headers: { "X-Requested-With": "XMLHttpRequest" }
          }
        )
        .then(response => console.log(response))
        .catch(error => console.log(error));
    }
  }
};
</script>