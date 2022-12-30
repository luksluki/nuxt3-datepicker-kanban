<template>
  <div class="container mx-auto px-4 pb-2">
    <div class="flex justify-start items-center py-4">
      <h1 class="text-2xl text-white mr-4">
        {{ moment(month).format("MMMM YYYY") }}
      </h1>

      <Datepicker v-model="month" month-picker>
        <template #trigger>
          <button
            class="w-12 h-12 bg-[#313439] text-gray-400 hover:text-white font-bold p-2 rounded-full"
          >
            <font-awesome-icon icon="fa-solid fa-calendar" />
          </button>
        </template>
      </Datepicker>
    </div>
    <div
      v-if="loading"
      class="container mx-auto flex items-center justify-center mb-8"
      role="status"
    >
      <svg
        aria-hidden="true"
        class="mr-2 w-8 h-8 text-gray-200 animate-spin dark:text-gray-600 fill-gray-600"
        viewBox="0 0 100 101"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z"
          fill="currentColor"
        />
        <path
          d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z"
          fill="currentFill"
        />
      </svg>
      <span class="sr-only">Loading...</span>
    </div>
    <div v-else>
      <Swiper
        :style="[
          { '--swiper-navigation-color': '#9CA3AF' },
          { '--swiper-navigation-size': '25px' },
        ]"
        class="text-white"
        :modules="modules"
        :slides-per-view="7"
        :space-between="50"
        :navigation="true"
        :breakpoints="{
          '300': {
            slidesPerView: 3,
            spaceBetween: 20,
          },
          '640': {
            slidesPerView: 4,
            spaceBetween: 20,
          },
          '768': {
            slidesPerView: 5,
            spaceBetween: 40,
          },
          '1024': {
            slidesPerView: 7,
            spaceBetween: 50,
          },
        }"
        @swiper="onSwiper"
        @slideChange="onSlideChange"
      >
        <SwiperSlide
          v-for="(day, i) in days"
          :key="i"
          class="px-2 p-4 flex justify-center"
        >
          <div
            class="flex justify-start group text-gray-400 hover:text-white active:text-white"
          >
            <div class="mt-6">
              <ol class="border-l-2 border-gray-400 group-hover:border-white">
                <li>
                  <div class="flex flex-start items-center">
                    <div
                      class="bg-gray-400 group-hover:bg-white w-4 h-4 flex items-center justify-center rounded-full -ml-2 mr-3 -mt-2"
                    ></div>
                  </div>
                  <div class="ml-6 mb-6 pb-6"><br /></div>
                </li>
              </ol>
            </div>
            <div class="">
              <p class="text-5xl">{{ moment(day).format("D") }}</p>
              <span>{{ moment(day).format("dddd") }}</span>
            </div>
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </div>
</template>

<script setup>
import { Pagination, Navigation } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import Datepicker from "@vuepic/vue-datepicker";
import "@vuepic/vue-datepicker/dist/main.css";
import moment from "moment";
const modules = ref([Pagination, Navigation]);

// Import Swiper styles
import "swiper/css";
import "swiper/css/pagination";
import "swiper/css/navigation";

const loading = ref(false);
const days = ref([]);
const width = ref(0);
const month = ref({
  month: new Date().getMonth(),
  year: new Date().getFullYear(),
});

const onSwiper = (swiper) => {
  console.log(swiper);
};
const onSlideChange = () => {
  console.log("slide change");
};

function getDaysInMonth() {
  const date = new Date();
  const month = date.getMonth();
  const year = date.getFullYear();
  const firstDayOfMonth = new Date(year, month, -2);
  const firstDayOfWeek = firstDayOfMonth.getDay();
  const lastDayOfMonth = new Date(year, month + 1, 0).getDate();
  const dates = [];
  for (let day = firstDayOfWeek; day <= lastDayOfMonth; day++) {
    const date = new Date(year, month, day);
    dates.push(date);
  }
  days.value = dates;
}

function resetDays() {
  loading.value = true;
  setTimeout(() => {
    let date = new Date(Date.UTC(month.value.year, month.value.month, 1));
    let dates = [];
    while (date.getUTCMonth() === month.value.month) {
      dates.push(new Date(date));
      date.setUTCDate(date.getUTCDate() + 1);
    }
    days.value = dates;
    loading.value = false;
  }, 500);
}

function updateScreenWidth() {
  width.value = window.innerWidth;
}

onMounted(() => {
  getDaysInMonth();
  window.addEventListener("resize", updateScreenWidth());
});

onUnmounted(() => {
  window.removeEventListener("resize", updateScreenWidth());
});

watch(month, async (newMonth, oldMonth) => {
  resetDays();
});
</script>
