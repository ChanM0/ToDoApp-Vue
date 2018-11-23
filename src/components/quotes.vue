<template>
  <div>
    <button class="btn btn-primary" @click="onGetQuotes">Get Quotes</button>
    <hr>
    <app-quote v-form="quote in quotes" :qt="quote"></app-quote>
  </div>
</template>

<script>
import Quote from "./quote.vue";
import axios from "axios";

export default {
  data() {
    return {
      quotes: []
    };
  },
  methods(){
    onGetQuotes(){
      var path =
        "http://localhost:8888/ApplicationCreation/ToDoApp/public/api/quotes";
      axios
        .get(path)
        .then(response => {
          console.log(response);

        })
        .catch(error => console.log(error));
    }
  },
  components: {
    "app-quote": Quote
  }
};
</script>