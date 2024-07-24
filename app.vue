<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-900">
    <div class="w-[400px] bg-gray-800 rounded-3xl py-6 ps-6 text-white">
      <h1 class="text-2xl font-bold mb-4">Profile</h1>
      <div class="relative slider w-full overflow-hidden">
        <div class="relative w-[85%] h-[250px] mb-4 overflow-hidden rounded-3xl">
          <div class="flex transition-transform duration-300 ease-in-out"
               :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
            <div v-for="image in images" class="flex-shrink-0 w-full h-[250px]">
              <img :src="image" class="w-full h-full object-cover" alt="Slider"/>
            </div>

          </div>
          <button @click="prevSlide"
                  class="absolute left-2 top-1/2 transform -translate-y-1/2
                  h-[35px] w-[35px] bg-[#232121]/60 backdrop-grayscale-0 border border-main_dark-700 text-white px-3 py-1 rounded-[5px] flex justify-center items-center">
            <
          </button>
          <button @click="nextSlide"
                  class="absolute right-2 top-1/2 transform -translate-y-1/2
                  h-[35px] w-[35px] bg-[#232121]/60 backdrop-grayscale-0 border border-main_dark-700 text-white px-3 py-1 rounded-[5px] flex justify-center items-center">
            >
          </button>
        </div>
        <div class="next absolute top-0  w-full bottom-0 -right-[90%]">
          <div class="relative w-full h-[250px]">
            <img :src="images[nextIndex]" class=" w-full h-full rounded-3xl" alt="next image"/>
            <div class="absolute inset-0 backdrop-blur-[5px] bg-black bg-opacity-30 rounded-3xl"/>
          </div>
        </div>
        <h2 class="text-2xl font-bold mb-1">Cristiano Ronaldo</h2>
        <p class="text-gray-400 mb-4">Football Player</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        'https://images.unsplash.com/photo-1721396181274-cd0c9a5f7133?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
        'https://images.unsplash.com/photo-1721807578532-dc1756624727?q=80&w=2500&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
      ],
      currentIndex: 0,
      nextIndex: 1,
    }
  },
  methods: {
    prevSlide() {
      this.nextIndex = this.currentIndex;
      this.currentIndex = (this.currentIndex + this.images.length - 1) % this.images.length;
    },
    nextSlide() {
      this.nextIndex = this.nextIndex === this.images.length - 1 ? 0 : this.nextIndex + 1;
      this.currentIndex = this.currentIndex === this.images.length - 1 ? 0 : this.currentIndex + 1
    },
  },
}
</script>
