<script setup>
import { ref, defineEmits } from "vue";
import closeIcon from "@/assets/icons/CloseRounded.png";

const searchQuery = ref("");
const inputFocused = ref(false);
const emit = defineEmits(["updateSearch"]);

const clearSearch = () => {
  searchQuery.value = "";
  emit("updateSearch", searchQuery.value);
};

const handleInput = () => {
  emit("updateSearch", searchQuery.value);
};
</script>

<template>
  <div class="relative mt-4">
    <input
      type="text"
      v-model="searchQuery"
      @focus="inputFocused = true"
      @blur="inputFocused = false"
      @input="handleInput"
      class="w-full p-2 pl-4 pr-10 border-2 rounded-[2px] bg-white text-black focus:outline-none"
      :class="{
        'border-gray-500': inputFocused,
        'border-gray-300': !inputFocused,
      }"
      placeholder="Search..."
    />
    <button
      v-if="searchQuery"
      @click="clearSearch"
      class="absolute right-2 top-2 text-gray-500 hover:text-gray-700"
    >
      <img
        :src="closeIcon"
        alt="Close"
        class="h-[20px] w-[20px] object-contain"
      />
    </button>
  </div>
</template>

<style scoped>
input:invalid {
  box-shadow: none;
}
</style>
