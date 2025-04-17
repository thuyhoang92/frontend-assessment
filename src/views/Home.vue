<template>
  <div class="max-w-7xl mx-auto px-4 py-8">
    <div class="text-center mb-16 animate-fadeIn">
      <h1
        class="text-5xl font-bold mb-4 text-[#2c3e50] inline-block relative after:content-[''] after:absolute after:bottom-[-10px] after:left-1/2 after:-translate-x-1/2 after:w-[100px] after:h-1 after:bg-gradient-to-r after:from-[#4a90e2] after:to-[#9b59b6] after:rounded">
        Frontend Assessment</h1>
      <p class="text-xl text-[#7f8c8d]">Welcome to the frontend assessment exercises</p>
    </div>

    <div class="flex flex-wrap gap-8 justify-center mt-8 md:flex-row flex-col items-stretch">
      <div
        class="flex-1 min-w-[300px] max-w-[450px] w-full bg-white rounded-xl overflow-hidden shadow-md transition-all duration-300 hover:transform hover:-translate-y-1 hover:shadow-lg flex">
        <router-link to="/exercise1" class="flex p-8 text-inherit no-underline w-full">
          <div class="flex-shrink-0 w-[60px] h-[60px] bg-[#f0f5ff] rounded-xl flex items-center justify-center mr-6">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-[30px] h-[30px] text-[#4a90e2]">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
            </svg>
          </div>
          <div class="flex-1">
            <h2 class="text-2xl font-semibold mb-2 text-[#2c3e50]">Exercise 1</h2>
            <p class="text-[#7f8c8d] text-base">Build a responsive page based on the designs.</p>
          </div>
        </router-link>
      </div>

      <div
        class="flex-1 min-w-[300px] max-w-[450px] w-full bg-white rounded-xl overflow-hidden shadow-md transition-all duration-300 hover:transform hover:-translate-y-1 hover:shadow-lg flex">
        <router-link to="/exercise2" class="flex p-8 text-inherit no-underline w-full">
          <div class="flex-shrink-0 w-[60px] h-[60px] bg-[#f0f5ff] rounded-xl flex items-center justify-center mr-6">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-[30px] h-[30px] text-[#4a90e2]">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
            </svg>
          </div>
          <div class="flex-1">
            <h2 class="text-2xl font-semibold mb-2 text-[#2c3e50]">Exercise 2</h2>
            <p class="text-[#7f8c8d] text-base">Read the data.json file and display the data as tabs on desktop and an
              accordion on mobile.</p>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style lang="scss" scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeIn {
  animation: fadeIn 0.8s ease-out;
}
</style>
