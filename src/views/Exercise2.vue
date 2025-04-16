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
    
    <!-- Bonus: Explanation of JavaScript quirk -->
    <div class="mt-12 p-6 bg-gray-50 rounded-lg shadow-sm">
      <h2 class="text-2xl font-semibold mb-4 text-gray-800">Bonus Explanation</h2>
      <p class="mb-4">Why is the result of <code class="bg-gray-200 px-2 py-1 rounded text-sm font-mono">('b' + 'a' + + 'a' + 'a').toLowerCase()</code> "banana"?</p>
      <div class="mt-4">
        <p class="mb-2">This expression evaluates to "banana" because:</p>
        <ol class="ml-6 mb-4 list-decimal">
          <li class="mb-2 transition-transform duration-200 hover:translate-x-1">'b' + 'a' = "ba" (string concatenation)</li>
          <li class="mb-2 transition-transform duration-200 hover:translate-x-1">+ 'a' = NaN (the unary plus operator tries to convert 'a' to a number but fails, resulting in NaN)</li>
          <li class="mb-2 transition-transform duration-200 hover:translate-x-1">"ba" + NaN = "baNaN" (NaN is coerced to the string "NaN")</li>
          <li class="mb-2 transition-transform duration-200 hover:translate-x-1">"baNaN" + 'a' = "baNaNa" (string concatenation)</li>
          <li class="mb-2 transition-transform duration-200 hover:translate-x-1">"baNaNa".toLowerCase() = "banana" (converts to lowercase)</li>
        </ol>
        <p>It's a quirky result due to JavaScript's type coercion and the way the unary plus operator works!</p>
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