<template>
  <div>
    <h2>Sample Models Menu for Reveal team</h2>

    <ul>
      <li v-for="algo in algos" :key="algo.id">
        {{algo.name}} ({{algo.version}}) <a :href="algo.docs_link">docs</a> - {{algo.description}}
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'ListAlgos',
    data() {
      return {
        algos: []
      }
    },
    async mounted() {
      const res = await axios('http://389d28f4.ngrok.io/algos')
      this.algos = res.data
    }
  }
</script>

<style scoped>

</style>