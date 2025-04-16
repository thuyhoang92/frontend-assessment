<template>
  <div class="exercise2 container mx-auto">
    <h1 class="exercise2__title max-w-4xl mx-auto text-center text-gray-800 py-4">Exercise 2 - Tabs & Accordion</h1>
    
    <!-- Desktop Tabs -->
    <div class="tabs bg-white rounded-lg shadow-md overflow-hidden px-4" v-if="!isMobile">
      <div class="tabs__header">
        <div
          v-for="(item, index) in data"
          :key="index"
          class="tabs__item"
          :class="{ 'tabs__item--active': activeTab === index }"
          @click="toggleTab(index)"
        >
          {{ item.title }}
        </div>
      </div>
      <div class="tabs__content">
        <div
          v-for="(item, index) in data"
          :key="index"
          class="tabs__panel"
          :class="{ 'tabs__panel--active': activeTab === index }"
          v-show="activeTab === index"
        >
          <div v-html="item.content"></div>
        </div>
      </div>
    </div>
    
    <!-- Mobile Accordion -->
    <div class="accordion p-4" v-else>
      <div
        v-for="(item, index) in data"
        :key="index"
        class="accordion__item mb-4 rounded-lg overflow-hidden bg-white"
      >
        <div
          class="accordion__header"
          :class="{ 'accordion__header--active': activeTab === index }"
          @click="toggleTab(index)"
        >
          {{ item.title }}
          <span class="accordion__icon">
            {{ activeTab === index ? '−' : '+' }}
          </span>
        </div>
        <transition name="accordion">
          <div
            class="accordion__content"
            v-show="activeTab === index"
            v-html="item.content"
          ></div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import data from '../../data.json';

export default {
  name: 'Exercise2',
  data() {
    return {
      data,
      activeTab: 0,
      isMobile: false
    };
  },
  mounted() {
    this.checkScreenSize();
    window.addEventListener('resize', this.checkScreenSize);
    
    // Open first tab/accordion by default
    this.activeTab = 0;
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.checkScreenSize);
  },
  methods: {
    toggleTab(index) {
      // If clicking on currently open accordion, close it
      if (this.activeTab === index) {
        if (this.isMobile) {
          this.activeTab = -1; // Set to -1 to close all
        }
      } else {
        this.activeTab = index;
      }
    },
    checkScreenSize() {
      this.isMobile = window.innerWidth < 768;
      if (this.activeTab < 0 || this.activeTab >= this.data.length) {
        this.activeTab = 0;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@use "../assets/css/exercise2.scss";
</style> 