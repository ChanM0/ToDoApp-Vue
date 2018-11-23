 <template>
 <!-- the submit event will no longer reload the page -->
 <!-- @submit == v-on:event -->
   <form @submit.prevent="onSubmitted">
     <div class="form-group">
       <label for="content">Content</label>
       <!-- Vmodel allows to get the input the user enters here -->
       <input 
        type="text" 
        id="content" 
        class="form-control" 
        v-model="quoteContent"
        >
        <button class="btn btn-primary" type="submit">Submit </button>
     </div>
   </form>
 </template>
 
 <script>
import axios from "axios";
export default {
  data() {
    return {
      quoteContent: ""
    };
  },
  methods: {
    onSubmitted() {
      var path =
        "http://localhost:8888/ApplicationCreation/ToDoApp/public/api/quote";
      axios
        .post(path, { content: this.quoteContent })
        .then(response => console.log(response))
        .catch(error => console.log(error));
    }
  }
};
</script>