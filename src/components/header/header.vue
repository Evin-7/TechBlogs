<template>
  <div
    class="bg-[#f6f6f6] shadow-md pl-[50px] pr-[50px] font-poppins text-black p-4 flex items-center justify-between shadow-lg"
  >
    <!-- Logo on the left -->
    <img
      class="object-contain h-[60px] w-[120px]"
      src="../../assets/icons/TechBlogsMainLogo.png"
      alt="Tech Blogs Logo"
    />
    <!-- Sections on the right -->
    <div class="flex gap-6 text-sm font-medium">
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
export default {
  name: "Header",
};
</script>
