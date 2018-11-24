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
        .then(response => {
          console.log(response);
          const token = response.data.token;
          /** for decrypting the token  */
          // const base64url = token.split(".")[1];
          // const base64 = base64url.replace("-", "+").replace("_", "/");
          // console.log(JSON.parse(window.atob(base64)));
          localStorage.setItem("token", token);
        })
        .catch(error => console.log(error));
    }
  }
};
</script>