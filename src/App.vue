<template>
  <div id="app">
    <RecursiveAccordion :node="categories" />
  </div>
</template>

<script>
import RecursiveAccordion from './components/RecursiveAccordion'

export default {
  name: 'app',
  data () {
    return {
      categories: {
        title: 'Root Node',
        children: [
          {
            title: 'Child Node #1',
            children: [
              {
                title: 'Deep Child Node'
              }
            ]
          },
          {
            title: 'Child Node #2'
          }
        ]
      }
    }
  },
  components: {
    RecursiveAccordion
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
