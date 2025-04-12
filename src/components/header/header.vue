<template>
  <div
    class="bg-[#f6f6f6] shadow-md pl-[45px] pr-[50px] font-poppins text-black p-4 flex items-center justify-between shadow-lg"
  >
    <img
      class="object-contain h-[40px] w-[100px]"
      src="../../assets/icons/TechBlogsMainLogo.png"
      alt="Tech Blogs Logo"
    />
    <div
      class="flex gap-4 text-lg font-medium"
      :class="{ hidden: isMobile, flex: !isMobile }"
    >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Home</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Articles</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Tutorials</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Contact</a
      >
    </div>

    <button v-if="isMobile" @click="toggleMenu" class="text-gray-600">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4 6h16M4 12h16M4 18h16"
        />
      </svg>
    </button>
    <div
      v-if="isMenuOpen && isMobile"
      class="absolute top-[70px] right-0 bg-[#f6f6f6] p-4 rounded-md shadow-md flex flex-col gap-2"
    >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Home</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Articles</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Tutorials</a
      >
      <a href="#" class="hover:text-green-600 transition-colors duration-200"
        >Contact</a
      >
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from "vue";

export default {
  name: "Header",
  setup() {
    const isMobile = ref(window.innerWidth < 768);
    const isMenuOpen = ref(false);

    const handleResize = () => {
      isMobile.value = window.innerWidth < 768;
      if (!isMobile.value) {
        isMenuOpen.value = false;
      }
    };

    const toggleMenu = () => {
      isMenuOpen.value = !isMenuOpen.value;
    };

    onMounted(() => {
      window.addEventListener("resize", handleResize);
    });

    onUnmounted(() => {
      window.removeEventListener("resize", handleResize);
    });

    return {
      isMobile,
      isMenuOpen,
      toggleMenu,
    };
  },
};
</script>
