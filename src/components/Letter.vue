<template>
  <div
    class="absolute left-1/2 top-1/2 w-full max-w-[90%] sm:max-w-[700px] aspect-[1.4/1] rounded-lg p-6 flex items-center justify-center cursor-pointer transform -translate-x-1/2 -translate-y-1/2"
  >
    <!-- Briefcontainer -->
    <div
      v-if="!clickedYes"
      class="w-[400px] h-[500px] bg-[#F9A8D4] rounded-lg shadow-lg flex flex-col items-center justify-center text-center p-8 pt-16"
    >
      <h1 class="text-4xl font-bold text-[#E74C3C] mb-6">
        Willst du mein Valentinsdate sein?
      </h1>
      <button
        @click="handleYes"
        class="px-6 py-3 bg-[#E74C3C] text-white font-bold text-lg rounded-lg shadow-md hover:bg-[#c0392b] transition-transform duration-200 transform hover:scale-105 mb-4"
      >
        Ja!
      </button>
      <button
        @mouseover="moveButton"
        :style="{
          top: buttonPosition.top + 'px',
          left: buttonPosition.left + 'px',
        }"
        class="absolute px-4 py-2 bg-white text-[#E74C3C] font-medium text-sm rounded-lg shadow-sm hover:bg-gray-100 transition-colors duration-200"
      >
        Nein
      </button>
    </div>
    <div v-if="clickedYes">
      <div
        class="w-[400px] cursor-auto h-[500px] bg-[#F9A8D4] rounded-lg shadow-lg flex flex-col items-center justify-center text-center p-8"
      >
        <!-- Bild -->
        <div class="mb-6">
          <img
            src="../assets/kiss.gif"
            alt="Bears"
            class="w-[200px] h-auto mx-auto rounded-md shadow-md"
          />
        </div>
        <!-- Titel -->
        <h1 class="text-4xl font-bold text-[#E74C3C] mb-4">Yay!</h1>
        <!-- Beschreibung -->
        <p class="text-lg text-gray-700 mb-6">Ich melde mich bei dir 😍</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import { ref } from "vue";
const clickedYes = ref(false);
const buttonPosition = reactive({ top: 300, left: 150 });

const moveButton = () => {
  const randomTop = Math.floor(Math.random() * 350) + 50; // Zufällige Position in einem Bereich
  const randomLeft = Math.floor(Math.random() * 300) + 50;
  buttonPosition.top = randomTop;
  buttonPosition.left = randomLeft;
};

const handleYes = () => {
  clickedYes.value = true;
  console.log("Wohoo! 🎉 Cooool! Ich melde mich bei dir!");
};
</script>

<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: scale(0.5);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.animate-fade-in {
  animation: fade-in 0.8s ease-out forwards;
}
</style>
