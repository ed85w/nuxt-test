<template>
  <div>
    <SearchJokes v-on:search-text="searchText"/>
    <Joke v-for="joke in jokes" :key="joke.id"
    :id="joke.id" :joke="joke.joke"/>
    <!--joke id and joke listed as props in Joke.vue -->
  </div>
</template>

<script>
import axios from "axios";
import Joke from '../../components/Joke'
import SearchJokes from '../../components/SearchJokes'

export default {
  components: {
    Joke,
    SearchJokes
  },
  data(){
    return{
      jokes: []
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
      const res = await axios.get('https://icanhazdadjoke.com/search', config);

      // console.log(res.data);
      this.jokes = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchText(text){
      const config = {
        headers: {
          'Accept': 'application/json'
        }
      }

      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config);

        // console.log(res.data);
        this.jokes = res.data.results;
      } catch (err) {
        console.log(err);
      }
    }
  },
  head(){
    return {
      title: 'Dad Jokes',
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