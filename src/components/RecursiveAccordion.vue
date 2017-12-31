<template>
  <div class="recursive-accordion">
    <h1>{{ node.title }}</h1>
    <RecursiveAccordion v-for="(child, childIndex) in node.children" :key="childIndex" :node="child" />
  </div>
</template>

<script>
export default {
  name: 'RecursiveAccordion',
  props: ['node']
}
</script>

<style>
</style>
