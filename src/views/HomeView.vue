<script setup>
import { ref } from "vue";
import Header from "@/components/header/Header.vue";
import SearchInput from "../components/search/SearchInput.vue";
import ArticleCard from "../components/articles/ArticleCard.vue";
import data from "../data/data.json";
import SearchResults from "../components/search/SearchResults.vue";

const searchQuery = ref("");

const updateSearch = (query) => {
  searchQuery.value = query;
};
</script>

<template>
  <div>
    <Header class="fixed top-0 left-0 w-full z-10" />
  </div>

  <div
    class="flex flex-wrap flex-col md:flex-row bg-white justify-center items-center pt-[50px] mt-[70px]"
  >
    <div
      class="w-full md:w-[93%] flex flex-col md:flex-row justify-center bg-[#D3D3D3] overflow-y-auto"
      :style="{ height: `calc(100vh - 70px)` }"
    >
      <div
        class="w-full md:w-[65%] p-[10px] md:p-[0px] md:pl-[55px] pt-[2000px] md:pt-[50px]"
      >
        <span class="font-bold text-[24px] md:text-[30px]">Search</span>
        <SearchInput @updateSearch="updateSearch" />
        <SearchResults :items="data" :searchQuery="searchQuery" />
      </div>

      <div
        class="w-full md:w-[35%] p-[10px] md:p-[0px] md:pl-[40px] font-poppins pr-[20px] md:pr-[40px] pt-[20px] md:pt-[40px]"
      >
        <ArticleCard />
      </div>
    </div>
  </div>
</template>

<style scoped>
.fixed {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
}

.overflow-y-auto {
  overflow-y: auto;
}
</style>
