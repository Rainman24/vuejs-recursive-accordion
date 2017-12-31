<template>
  <div class="recursive-accordion" :style="{paddingLeft: depth * 16 + 'px'}">
    <h1>{{ node.title }}</h1>
    <RecursiveAccordion
      v-for="(child, childIndex) in node.children" :key="childIndex"
      :node="child"
      :depth="depth + 1"
    />
  </div>
</template>

<script>
export default {
  name: 'RecursiveAccordion',
  props: {
    node: {
      type: Object
    },
    depth: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style>
</style>
