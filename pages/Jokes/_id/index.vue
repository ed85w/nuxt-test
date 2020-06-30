<!--for single joke - needs to be in folder called _id -->

<template>
  <div>
    single joke
    <h1>parameter = {{$route.params.id}}</h1>
    <hr>
    <h2>{{ joke}} </h2>
    <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(){
    return {
      joke: {}
    }
  },
  // using axios for api
  // https://icanhazdadjoke.com/api
  async created(){
    const config = {
      headers: {
        'Accept': 'application/json'
      }
    }

    try {
      //NOTE use of ` in get request
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);

      //res.data.joke comes from api
      this.joke = res.data.joke;
      console.log(this.joke)
    } catch (err) {
      console.log(err);
    }
  },
    head(){
    return {
      title: this.$route.params.id,
      meta: [
        {
          hid: 'description', //id
          description: 'description', //meta type
          content: 'this is the description' //meta content

        }
      ]
    };
  }
}
</script>

<style>

</style>