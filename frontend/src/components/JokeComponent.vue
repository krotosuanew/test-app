<template>
  <div>
    <h1>Random Joke</h1>
    <button @click="fetchJoke">Get a Joke</button>
    <p v-if="joke">{{ joke.setup }} - {{ joke.punchline }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      joke: null,
    };
  },
  methods: {
    async fetchJoke() {
      try {
        const response = await fetch('http://localhost:3000/api/joke');
        this.joke = await response.json();
      } catch (error) {
        console.error('Failed to fetch joke:', error);
      }
    },
  },
};
</script>
