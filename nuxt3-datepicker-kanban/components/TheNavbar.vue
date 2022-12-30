<template>
  <nav class="bg-gray-900 p-4 flex justify-between items-center shadow-md">
    <div class="flex items-center">
      <a href="#" class="font-bold text-white text-xl w-8 h-8">
        <img src="@/assets/img/logo.png" alt="Logo" class="w-8 h-8 mr-2" />
      </a>
      <div class="hidden lg:block">
        <NuxtLink
          v-for="(menu, i) in menus"
          :key="i"
          :to="menu.to"
          class="text-gray-400 hover:text-gray-100 rounded-full py-2 px-4"
          activeClass="text-gray-100 ::after"
        >
          {{ menu.title }}
        </NuxtLink>
      </div>
    </div>
    <div class="md:flex hidden space-x-4">
      <button
        v-for="icon in iconMenus"
        :key="icon.id"
        class="w-12 h-12 bg-[#313439] text-gray-400 hover:text-white font-bold py-2 px-4 rounded-full"
      >
        <font-awesome-icon :icon="icon" />
      </button>
    </div>

    <div class="block lg:hidden space-x-4">
      <button
        class="bg-[#313439] text-gray-400 hover:text-white font-bold py-2 px-4 rounded-lg"
      >
        <font-awesome-icon icon="fa-solid fa-bars" />
      </button>
    </div>
  </nav>
</template>

<script setup>
const menus = ref([
  {
    title: "Overview",
    to: "/",
  },
  {
    title: "Learn",
    to: "/learn",
  },
  {
    title: "Hub",
    to: "/hub",
  },
  {
    title: "Activity",
    to: "/activity",
  },
  {
    title: "Leaderboard",
    to: "/leaderboard",
  },
  {
    title: "Community",
    to: "/community",
  },
  {
    title: "Jobs",
    to: "/jobs",
  },
]);

const iconMenus = ref([
  "fa-solid fa-search",
  "fa-solid fa-message",
  "fa-solid fa-circle-question",
  "fa-solid fa-plus",
]);
</script>
