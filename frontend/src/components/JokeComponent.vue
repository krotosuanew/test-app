<template>
  <div>
    <h1>Random Joke</h1>
    <button @click="fetchJoke">Get a Joke</button>
    <p v-if="joke">{{ joke.setup }} - {{ joke.punchline }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      joke: null,
    };
  },
  methods: {
    async fetchJoke() {
      try {
        const response = await axios.get(`${import.meta.env.VITE_DOMAIN}/api/joke`);
        this.joke = response.data;
      } catch (error) {
        console.error('Failed to fetch joke:', error);
      }
    },
  },
};
</script>
