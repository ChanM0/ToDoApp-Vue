<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-xs-12">
          <router-link to="/">Quotes</router-link> | 
          <router-link to="/new-quote">New Quote</router-link> |
          <router-link to="/sign-up">Sign up</router-link> |
          <router-link to="/sign-in">Sign In</router-link> |
        </div>
      </div>
      <hr>
      <div class="row">
        <div class="col-xs-12">
          <router-view></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import NewQuote from "./components/new-quote.vue";
export default {
  name: "app",
  data() {
    return {};
  }
};
</script>

<style>
#app {
  margin: 30px;
}
</style>
