<template>
  <div id="app">
    <div class="target-container">
      <p>List of people:</p>
      <ul>
        <li v-for="(person, index) in people" :key="`person-${index}`">
          {{person}}
        </li>
      </ul>
      <div class="add-person">
        <input type="text" v-model="value" placeholder="Add Person" />
        <button @click="addPerson()">Add Person</button>
      </div>
      <button @click="exchange()">Exchange Gifts Now</button>
    </div>
    <div v-if="finalList && finalList.length" class="exchange-result-container">
      <ul>
        <li v-for="(pair, index) in finalList" :key="`pair-${index}`">
          {{pair.giver}} gives a gift to {{pair.receiver}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      people: ['Susan', 'Beth', 'Abe', 'Ardi', 'Quan'],
      value: '',
      finalList: [],
    }
  },
  methods: {
    /**
     * @function addPerson
     */
    addPerson () {
      let val = this.value;
      let people = this.people;
      if(val.trim() !== "") {
        people.push(val);
      } else {
        alert('Please enter a person name');
      }
      this.value = '';
    },
    exchange () {
      // Shuffle the group in random order
      const people = this.people.sort(() => Math.random() - 0.5);
      // Length of Array
      const total = this.people.length;
      this.finalList = [];
      // Exchange Gift and  store them in the final list.
      for (let i = 0; i < total; i++ ) {
        this.finalList.push({
          giver: people[i],
          receiver: (i === total - 1) ? people[0] : people[i+1]
        });
      }
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
  padding: 10px;
}

.target-container,
.add-person {
padding-bottom: 20px;
}
</style>
