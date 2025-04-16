<template>
  <div class="exercise2 container mx-auto">
    <h1 class="exercise2__title max-w-4xl mx-auto text-center text-gray-800 py-4">Exercise 2 - Tabs & Accordion</h1>
    
    <!-- Desktop Tabs -->
    <Tabs 
      v-if="!isMobile" 
      :items="data" 
      :initialActiveTab="activeTab"
      @tab-change="onTabChange" 
    />
    
    <!-- Mobile Accordion -->
    <Accordion 
      v-else 
      :items="data" 
      :initialActiveItem="activeTab"
      @item-change="onItemChange" 
    />
  </div>
</template>

<script>
import data from '../../data.json';
import Tabs from '@components/Tabs.vue';
import Accordion from '@components/Accordion.vue';

export default {
  name: 'Exercise2',
  components: {
    Tabs,
    Accordion
  },
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
    onTabChange(index) {
      this.activeTab = index;
    },
    onItemChange(index) {
      this.activeTab = index;
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