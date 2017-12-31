<template>
  <div class="recursive-accordion" :class="['recursive-accordion--depth-' + depth, {'recursive-accordion--has-children': node.children}]">
    <div class="recursive-accordion__item"
      @click="clickHandler"
      :style="{paddingLeft: (depth + 1) * 16 + 'px'}"
    >
      <span class="recursive-accordion__title">
        {{ node.title }}
        <i class="material-icons recursive-accordion__icon" v-if="node.children">
          {{ isOpen ? 'expand_less' : 'expand_more' }}
        </i>
      </span>
    </div>
    <div class="recursive-accordion__children" v-if="isOpen">
      <RecursiveAccordion
        v-for="(child, childIndex) in node.children" :key="childIndex"
        :node="child"
        :depth="depth + 1"
      />
    </div>
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
.recursive-accordion {
  max-width: 480px;
}

.recursive-accordion__item {
  padding: 16px 32px;
  transition: all 0.25s ease;
  background: #4d4d4f;
  color: white;
}

.recursive-accordion__item:hover {
  background: #404042;
}

.recursive-accordion__title {
  line-height: 24px;
  font-weight: 500;
  letter-spacing: 0.05em;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.recursive-accordion--has-children > .recursive-accordion__item:hover {
  cursor: pointer;
  background: #404042;
}

/* DEPTH 0 */
.recursive-accordion--depth-0 > .recursive-accordion__item {
  background: white;
  color: #4d4d4f;
}

.recursive-accordion--depth-0.recursive-accordion--has-children > .recursive-accordion__item:hover {
  background: #e8e8e8;
}

.recursive-accordion--depth-0 > .recursive-accordion__item > .recursive-accordion__title {
  text-transform: uppercase;
}

/* DEPTH 1 */
.recursive-accordion--depth-1 > .recursive-accordion__item {
  background: white;
  color: #4d4d4f;
}

.recursive-accordion--depth-1.recursive-accordion--has-children > .recursive-accordion__item:hover {
  background: #e8e8e8;
}

.recursive-accordion--depth-1 > .recursive-accordion__item > .recursive-accordion__title {
  text-transform: uppercase;
}

.recursive-accordion--depth-1 {
  border-top: solid 2px #888;
}

/* DEPTH 2 */
.recursive-accordion--depth-2 {
  border-top: solid 1px white;
}

.recursive-accordion--depth-2 > .recursive-accordion__item {
  background: #44b57b;
  color: white;
}

.recursive-accordion--depth-2 > .recursive-accordion__item:hover {
  background: #3da26e;
}

.recursive-accordion--depth-2 > .recursive-accordion__item > .recursive-accordion__title {
  text-transform: uppercase;
}
</style>
