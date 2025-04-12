<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  items: Array,
  searchQuery: String,
});

const currentPage = ref(1);
const itemsPerPage = 5;

const filteredItems = computed(() => {
  let results = props.items;

  if (props.searchQuery) {
    const query = props.searchQuery.toLowerCase();
    results = props.items
      .filter((item) => {
        return (
          item.heading.toLowerCase().includes(query) ||
          item.description.toLowerCase().includes(query) ||
          item.date.toLowerCase().includes(query)
        );
      })
      .slice(0, 10);
  }

  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return results.slice(start, end);
});

const totalPages = computed(() => {
  let totalItems = props.items.length;
  if (props.searchQuery) {
    const query = props.searchQuery.toLowerCase();
    totalItems = props.items
      .filter((item) => {
        return (
          item.heading.toLowerCase().includes(query) ||
          item.description.toLowerCase().includes(query) ||
          item.date.toLowerCase().includes(query)
        );
      })
      .slice(0, 10).length;
  }
  return Math.ceil(totalItems / itemsPerPage);
});

const goToPrevPage = () => {
  if (currentPage.value > 1) currentPage.value--;
};

const goToNextPage = () => {
  if (currentPage.value < totalPages.value) currentPage.value++;
};

const highlightText = (text) => {
  if (!props.searchQuery) return text;

  const query = props.searchQuery.toLowerCase();
  const index = text.toLowerCase().indexOf(query);

  if (index === -1) return text;

  const before = text.substring(0, index);
  const match = text.substring(index, index + props.searchQuery.length);
  const after = text.substring(index + props.searchQuery.length);

  return `${before}<span class="bg-yellow-200">${match}</span>${after}`;
};
</script>

<template>
  <div class="mt-6 space-y-4 pb-[100px] font-poppins">
    <div
      v-for="(item, index) in filteredItems"
      :key="index"
      class="bg-white p-4 rounded-lg shadow-md"
    >
      <h3
        class="text-lg font-semibold text-gray-800 mb-2"
        v-html="highlightText(item.heading)"
      ></h3>
      <h3 class="text-lg italic text-gray-800 mb-2">
        {{ item.date }}
      </h3>
      <p
        class="text-gray-600 mb-2"
        v-html="highlightText(item.description)"
      ></p>
    </div>

    <div v-if="totalPages > 1" class="flex justify-between items-center pt-4">
      <button
        @click="goToPrevPage"
        :disabled="currentPage === 1"
        class="px-4 py-2 bg-gray-300 rounded disabled:opacity-50"
      >
        Previous
      </button>

      <span class="text-sm text-gray-700">
        Page {{ currentPage }} of {{ totalPages }}
      </span>

      <button
        @click="goToNextPage"
        :disabled="currentPage === totalPages"
        class="px-4 py-2 bg-gray-300 rounded disabled:opacity-50"
      >
        Next
      </button>
    </div>

    <div
      v-if="searchQuery && filteredItems.length === 0"
      class="mt-6 text-center"
    >
      No matching results found.
    </div>
  </div>
</template>
