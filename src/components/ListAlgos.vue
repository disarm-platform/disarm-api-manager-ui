<template>
  <div>
    <h2>Sample Models Menu for Reveal team</h2>

    <ul>
      <li v-for="algo in algos" :key="algo._id">
        {{algo.name}}
        [ Versions:
        <span v-for="(release, index) in algo.releases" :key="release._id" >
          <a href="#">
            {{release.version}}
          </a>
          <span v-if="index + 1 != algo.releases.length">, </span>
        </span>
        ]
        - {{algo.description}}
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
      const res = await axios('https://disarm-api-manager.herokuapp.com/algos')
      this.algos = res.data
    }
  }
</script>

<style scoped>

</style>