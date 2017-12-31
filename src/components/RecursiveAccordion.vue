<template>
  <div class="recursive-accordion" :style="{paddingLeft: depth * 16 + 'px'}">
    <h1 @click="clickHandler">{{ node.title }}</h1>
    <template v-if="isOpen">
      <RecursiveAccordion
        v-for="(child, childIndex) in node.children" :key="childIndex"
        :node="child"
        :depth="depth + 1"
      />
    </template>
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
  },
  data () {
    return {
      isOpen: false
    }
  },
  methods: {
    clickHandler (event) {
      this.isOpen = !this.isOpen
    }
  }
}
</script>

<style>
</style>
