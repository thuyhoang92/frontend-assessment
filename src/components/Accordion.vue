<template>
  <div class="accordion p-4">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="accordion__item mb-4 rounded-lg overflow-hidden bg-white"
    >
      <div
        class="accordion__header"
        :class="{ 'accordion__header--active': activeItem === index }"
        @click="toggleItem(index)"
      >
        {{ item.title }}
        <span class="accordion__icon">
          {{ activeItem === index ? '−' : '+' }}
        </span>
      </div>
      <transition name="accordion">
        <div
          class="accordion__content"
          v-show="activeItem === index"
          v-html="item.content"
        ></div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Accordion',
  props: {
    items: {
      type: Array,
      required: true
    },
    initialActiveItem: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      activeItem: this.initialActiveItem
    };
  },
  methods: {
    toggleItem(index) {
      // If clicking on currently open accordion item, close it
      if (this.activeItem === index) {
        this.activeItem = -1; // Set to -1 to close all
      } else {
        this.activeItem = index;
      }
      this.$emit('item-change', this.activeItem);
    }
  }
};
</script>

<style lang="scss" scoped>
@use "../assets/css/exercise2.scss";
</style> 