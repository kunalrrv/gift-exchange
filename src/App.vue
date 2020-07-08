<template>
  <div id="app">
    <div class="target-container">
      <p>List of people:</p>
      <ul>
        <li v-for="(person, index) in people" :key="`person-${index}`">
          {{person}}
        </li>
      </ul>
      <button @click="exchange()">Exchange Gifts Now</button>
    </div>
    <div class="exchange-result-container">
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      people: ['Susan', 'Beth', 'Abe', 'Ardi', 'Quan']
    }
  },
  methods: {
    exchange () {
      console.log('Clicked');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
