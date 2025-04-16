<template>
  <header
    class="hero relative overflow-hidden w-full bg-gray-500 text-white text-center flex items-center justify-center">
    <picture>
      <source media="(min-width: 768px)" srcset="https://placehold.co/1920x650">
      <source media="(max-width: 767px)" srcset="https://placehold.co/600x600">
      <img src="https://placehold.co/1920x650" alt="Banner"
        class="hero__background absolute top-0 left-0 w-full h-full object-cover z-0">
    </picture>

    <div class="hero__content relative z-10 w-full max-w-7xl flex flex-col items-center justify-center">
      <div class="container mx-auto">
        <h2 class="hero__title text-5xl md:text-6xl font-bold mb-4 relative">Hello Developer!</h2>
        <p class="hero__subtitle text-base md:text-xl max-w-2xl mx-auto">Lorem ipsum dolor sit amet, consectetur
          adipiscing elit</p>
      </div>
    </div>
  </header>

  <main class="container mx-auto px-4 py-4 md:py-12">
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="card" v-for="(card, index) in cards" :key="index">
        <img :src="card.image" alt="Placeholder Image" class="card__image">
        <div class="card__content">
          <p class="card__text">
            {{ card.text }}
          </p>
          <div class="card__button-container">
            <a href="#" class="card__button transition-colors">READ MORE</a>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Exercise1',
  data() {
    return {
      cards: [
        {
          image: 'https://placehold.co/400x300',
          text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.'
        },
        {
          image: 'https://placehold.co/400x300',
          text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
        },
        {
          image: 'https://placehold.co/400x300',
          text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco.'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@use "../assets/css/exercise1.scss";
</style>