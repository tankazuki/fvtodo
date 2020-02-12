// Home.vue
<template>
  <div>
    <p>HomePage</p>
    <p>Random number from backend: {{ randomNumber }}</p>
    <button @click="getRandom">New Random Number</button> 
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      randomNumber: 0
    }
  },
  methods: {
    getRandom () {
      const path = 'http://localhost:5000/api/random'
      axios.get(path)
      .then(response => {
        this.randomNumber = response.data.randomNumber
      })
      .catch(error => {
        console.log(error)
      })
    }
  },
  created () {
    this.getRandom()
  }
}
</script>
