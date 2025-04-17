<template>
  <div class="tabs bg-white rounded-lg shadow-md overflow-hidden md:mx-6">
    <div class="tabs__header">
      <div
        v-for="(item, index) in items"
        :key="index"
        class="tabs__item"
        :class="{ 'tabs__item--active': activeTab === index }"
        @click="selectTab(index)"
      >
        {{ item.title }}
      </div>
    </div>
    <div class="tabs__content">
      <div
        v-for="(item, index) in items"
        :key="index"
        class="tabs__panel"
        :class="{ 'tabs__panel--active': activeTab === index }"
        v-show="activeTab === index"
      >
        <div v-html="item.content"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tabs',
  props: {
    items: {
      type: Array,
      required: true
    },
    initialActiveTab: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      activeTab: this.initialActiveTab
    };
  },
  methods: {
    selectTab(index) {
      this.activeTab = index;
      this.$emit('tab-change', index);
    }
  }
};
</script>

<style lang="scss" scoped>
@use "../assets/css/exercise2.scss";
</style> 