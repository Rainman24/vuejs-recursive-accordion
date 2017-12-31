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
                title: 'Deep Child Node #1',
                children: [
                  {
                    title: 'Deepest Child Node #1'
                  },
                  {
                    title: 'Deepest Child Node #2'
                  }
                ]
              },
              {
                title: 'Deep Child Node #2',
                children: [
                  {
                    title: 'Deepest Child Node #1'
                  },
                  {
                    title: 'Deepest Child Node #2'
                  }
                ]
              }
            ]
          },
          {
            title: 'Child Node #2',
            children: [
              {
                title: 'Deep Child Node'
              }
            ]
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
html,
body {
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Rubik', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.material-icons {
  vertical-align: middle;
}
</style>
