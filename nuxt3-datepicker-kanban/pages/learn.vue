<template>
  <div>
    <div class="w-full bg-gray-900"><DatePicker /></div>
    <div class="w-full bg-[#FAFAFA]">
      <div class="container mx-auto px-4 grid grid-cols-4 gap-4">
        <div class="col-span-1 py-4">
          <h1 class="text-2xl text-gray-900 mb-4 font-bold">Today</h1>
          <p class="text-sm text-gray-400 mb-2">Courses</p>
          <draggable
            v-model="courseData"
            group="people"
            @start="drag = true"
            @end="drag = false"
            item-key="id"
          >
            <template #item="{ element }">
              <div
                class="flex items-center justify-between rounded-lg shadow-lg bg-white p-6"
              >
                <div class="flex items-center">
                  <button
                    :class="`w-12 h-12 rounded-full bg-gray-100`"
                  ></button>
                  <div class="ml-4">
                    <h2 class="text-l font-bold text-gray-800">
                      {{ element.title }}
                    </h2>
                    <p class="text-gray-400">Stage {{ element.stage }}</p>
                  </div>
                </div>
                <font-awesome-icon icon="fa-solid fa-ellipsis" />
              </div>
            </template>
          </draggable>

          <p class="text-sm text-gray-400 mt-4 mb-2">Additional</p>
          <draggable
            v-model="additionalData"
            group="additional"
            @start="drag = true"
            @end="drag = false"
            item-key="id"
          >
            <template #item="{ element }">
              <div
                class="flex items-center justify-between rounded-lg shadow-lg bg-white p-6"
              >
                <div class="flex items-center">
                  <button
                    :class="`w-12 h-12 rounded-full bg-gray-100`"
                  ></button>
                  <div class="ml-4">
                    <h2 class="text-l font-bold text-gray-800">
                      {{ element.title }}
                    </h2>
                    <p class="text-gray-400">{{ element.stage }}</p>
                  </div>
                </div>
                <font-awesome-icon icon="fa-solid fa-ellipsis" />
              </div>
            </template>
          </draggable>
        </div>
        <div class="col-span-3 py-4">
          <h1 class="text-2xl text-gray-900 mr-4 font-bold">TimeTable</h1>
          <div class="overflow-x-auto relative flex items-center rounded-lg">
            <table class="w-full">
              <tr class="grid grid-cols-4">
                <th class="col-span-1">
                  <p class="text-sm text-gray-400 mt-4 mb-2">17:00</p>
                </th>
                <th class="col-span-1">
                  <p class="text-sm text-gray-400 mt-4 mb-2">18:00</p>
                </th>
                <th class="col-span-1">
                  <p class="text-sm text-gray-400 mt-4 mb-2">19:00</p>
                </th>
                <th class="col-span-1">
                  <p class="text-sm text-gray-400 mt-4 mb-2">20:00</p>
                </th>
              </tr>
              <tr class="grid grid-cols-4">
                <td class="col-span-1">
                  <draggable
                    v-model="timeTableData17"
                    group="additional"
                    @start="drag = true"
                    @end="drag = false"
                    item-key="id"
                  >
                    <template #item="{ element }">
                      <div :class="`rounded-lg shadow-lg bg-gray-100 p-4`">
                        <span
                          class="px-4 py-2 mb-4 rounded-full text-gray-400 bg-gray-200 font-semibold text-sm flex align-center w-max cursor-pointer active:bg-gray-300 transition duration-300 ease"
                        >
                          {{ element.stage }}
                        </span>
                        <div class="">
                          <h2 class="text-l font-bold text-gray-800">
                            {{ element.title }}
                          </h2>
                          <p class="text-gray-400">{{ element.stage }}</p>
                        </div>
                      </div>
                    </template>
                  </draggable>
                </td>
                <td class="col-span-1">
                  <draggable
                    v-model="timeTableData18"
                    group="additional"
                    @start="drag = true"
                    @end="drag = false"
                    item-key="id"
                  >
                    <template #item="{ element }">
                      <div :class="`rounded-lg shadow-lg bg-gray-100 p-4`">
                        <span
                          class="px-4 py-2 mb-4 rounded-full text-gray-400 bg-gray-200 font-semibold text-sm flex align-center w-max cursor-pointer active:bg-gray-300 transition duration-300 ease"
                        >
                          {{ element.stage }}
                        </span>
                        <div class="">
                          <h2 class="text-l font-bold text-gray-800">
                            {{ element.title }}
                          </h2>
                          <p class="text-gray-400">{{ element.stage }}</p>
                        </div>
                      </div>
                    </template>
                  </draggable>
                </td>
                <td class="col-span-1">
                  <draggable
                    v-model="timeTableData19"
                    group="additional"
                    @start="drag = true"
                    @end="drag = false"
                    item-key="id"
                  >
                    <template #item="{ element }">
                      <div :class="`rounded-lg shadow-lg bg-gray-100 p-4`">
                        <span
                          class="px-4 py-2 mb-4 rounded-full text-gray-400 bg-gray-200 font-semibold text-sm flex align-center w-max cursor-pointer active:bg-gray-300 transition duration-300 ease"
                        >
                          {{ element.stage }}
                        </span>
                        <div class="">
                          <h2 class="text-l font-bold text-gray-800">
                            {{ element.title }}
                          </h2>
                          <p class="text-gray-400">{{ element.stage }}</p>
                        </div>
                      </div>
                    </template>
                  </draggable>
                </td>
                <td class="col-span-1">
                  <draggable
                    v-model="timeTableData20"
                    group="additional"
                    @start="drag = true"
                    @end="drag = false"
                    item-key="id"
                  >
                    <template #item="{ element }">
                      <div :class="`rounded-lg shadow-lg bg-gray-100 p-4`">
                        <span
                          class="px-4 py-2 mb-4 rounded-full text-gray-400 bg-gray-200 font-semibold text-sm flex align-center w-max cursor-pointer active:bg-gray-300 transition duration-300 ease"
                        >
                          {{ element.stage }}
                        </span>
                        <div class="">
                          <h2 class="text-l font-bold text-gray-800">
                            {{ element.title }}
                          </h2>
                          <p class="text-gray-400">{{ element.stage }}</p>
                        </div>
                      </div>
                    </template>
                  </draggable>
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import draggable from "vuedraggable";

const drag = ref(false);
const courseData = ref([
  {
    title: "English Level CI",
    stage: "38/70",
    color: "#9FF3BB",
  },
  {
    title: "UI/UX design Advanced",
    stage: "37/123",
    color: "#6189B0",
  },
]);

const additionalData = ref([
  {
    title: "Speaking Club",
    stage: "7.30-8.15",
    color: "#EEEDF5",
  },
  {
    title: "Create a cool portofolio",
    stage: "18.45-8.50",
    color: "#DEEADE",
  },
]);

const timeTableData17 = ref([]);

const timeTableData18 = ref([
  {
    title: "Practice: writing and talking",
    stage: "17.30-18.30",
    color: "#9FEDB1",
  },
]);

const timeTableData19 = ref([
  {
    title: "Create a cool portofolio",
    stage: "18.45-8.50",
    color: "#DEEADE",
  },
]);

const timeTableData20 = ref([
  {
    title: "Interface animation and principle",
    stage: "18.45-8.50",
    color: "#99C0FB",
  },
]);
</script>
