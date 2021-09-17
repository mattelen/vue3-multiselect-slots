<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <multiselect
      v-model="value"
      :options="options"
      :multiple="false"
      track-by="library"
      :custom-label="customLabel"
  >
    <template v-slot:singleLabel="{ option }">You selected <strong>{{ option.library }}</strong></template>
  </multiselect>
  <pre>{{ value }}</pre>
</template>

<script>
import multiselect from 'vue-multiselect';

export default {
  name: 'App',
  components: {
    multiselect
  },
  data() {
    return {
      value: {language: 'JavaScript', library: 'Vue-Multiselect'},
      options: [
        {language: 'JavaScript', library: 'Vue.js'},
        {language: 'JavaScript', library: 'Vue-Multiselect'},
        {language: 'JavaScript', library: 'Vuelidate'}
      ]
    }
  },
  methods: {
    customLabel(option) {
      return `${option.library} - ${option.language}`
    }
  }
}
</script>

<style lang="scss">
@import '~vue-multiselect/dist/vue-multiselect.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
