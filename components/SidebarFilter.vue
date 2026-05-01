<template>
  <aside class="w-full flex flex-col gap-4 sticky top-5 h-fit">
    <!-- Search -->
    <div class="bg-white p-4 rounded-2xl">
      <h3 class="text-sm font-semibold mb-3">فیلتر و جستجو</h3>

      <div
        class="flex items-center h-10 border-2 border-[#ff2c6d] rounded-2xl px-3 bg-white gap-2"
      >
        <div class="flex items-center justify-center">
          <!-- search icon -->
          <svg viewBox="0 0 24 24" width="18" height="18">
            <circle
              cx="11"
              cy="11"
              r="7"
              stroke="#ff2c6d"
              stroke-width="2"
              fill="none"
            />
            <line
              x1="20"
              y1="20"
              x2="16.5"
              y2="16.5"
              stroke="#ff2c6d"
              stroke-width="2"
              stroke-linecap="round"
            />
          </svg>
        </div>

        <span class="w-px h-5 bg-gray-200"></span>

        <div class="relative flex-1">
          <input
            v-model="search"
            type="text"
            class="w-full bg-transparent outline-none text-sm text-right placeholder:text-gray-400 pr-1"
            placeholder="دو لنگه"
          />

          <button
            v-if="search"
            @click="search = ''"
            class="absolute left-0 top-1/2 -translate-y-1/2 bg-[#ffe5ed] w-5 h-5 flex items-center justify-center rounded-full cursor-pointer"
          >
            <svg viewBox="0 0 24 24" width="14" height="14">
              <path
                d="M6 6L18 18M18 6L6 18"
                stroke="#7A8898"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>
          </button>
        </div>
      </div>

      <button
        class="mt-3 w-full h-10 rounded-xl bg-gradient-to-r from-[#ff0057] to-[#ff2c6d] text-white text-sm"
      >
        جستجو
      </button>
    </div>

    <!-- Available Toggle -->
    <div
      class="bg-white p-4 rounded-2xl flex items-center justify-between text-sm"
    >
      <span>درب‌های موجود</span>

      <label class="relative w-10 h-5 cursor-pointer">
        <input type="checkbox" v-model="availableOnly" class="peer hidden" />

        <span
          class="absolute inset-0 bg-gray-300 rounded-full transition-all peer-checked:bg-[#ff2c6d]"
        ></span>

        <span
          class="absolute top-0.5 right-0.5 w-4 h-4 rounded-full bg-white transition-all peer-checked:translate-x-[-18px]"
        ></span>
      </label>
    </div>

    <!-- Sort -->
    <div class="bg-white p-4 rounded-2xl">
      <div
        class="flex justify-between items-center text-sm font-semibold cursor-pointer"
        @click="sortOpen = !sortOpen"
      >
        <span>مرتب سازی</span>

        <svg
          class="transition-transform duration-200"
          :class="{ 'rotate-180': sortOpen }"
          width="18"
          height="18"
          viewBox="0 0 24 24"
        >
          <path
            d="M6 9l6 6 6-6"
            stroke="#444"
            stroke-width="2"
            fill="none"
            stroke-linecap="round"
          />
        </svg>
      </div>

      <transition name="accordion">
        <div v-show="sortOpen">
          <label class="flex items-center gap-2 mt-2 text-xs">
            <input type="radio" class="hidden" value="low" v-model="sort" />
            <span
              class="w-4 h-4 border-2 border-gray-400 rounded-full relative radio-dot"
            ></span>
            تعداد: کم به زیاد
          </label>

          <label class="flex items-center gap-2 mt-2 text-xs">
            <input type="radio" class="hidden" value="high" v-model="sort" />
            <span
              class="w-4 h-4 border-2 border-gray-400 rounded-full relative radio-dot"
            ></span>
            تعداد: زیاد به کم
          </label>

          <label class="flex items-center gap-2 mt-2 text-xs">
            <input
              type="radio"
              class="hidden"
              value="rankHigh"
              v-model="sort"
            />
            <span
              class="w-4 h-4 border-2 border-gray-400 rounded-full relative radio-dot"
            ></span>
            رتبه: زیاد به کم
          </label>

          <label class="flex items-center gap-2 mt-2 text-xs">
            <input type="radio" class="hidden" value="rankLow" v-model="sort" />
            <span
              class="w-4 h-4 border-2 border-gray-400 rounded-full relative radio-dot"
            ></span>
            رتبه: کم به زیاد
          </label>
        </div>
      </transition>
    </div>

    <!-- Categories -->
    <div class="bg-white p-4 rounded-2xl">
      <div
        class="flex justify-between items-center text-sm font-semibold cursor-pointer"
        @click="categoryOpen = !categoryOpen"
      >
        <span>دسته بندی</span>

        <svg
          class="transition-transform duration-200"
          :class="{ 'rotate-180': categoryOpen }"
          width="18"
          height="18"
          viewBox="0 0 24 24"
        >
          <path
            d="M6 9l6 6 6-6"
            stroke="#444"
            stroke-width="2"
            fill="none"
            stroke-linecap="round"
          />
        </svg>
      </div>

      <transition name="accordion">
        <div v-show="categoryOpen">
          <!-- item -->
          <label class="flex justify-between items-center mt-3 text-sm">
            <div class="flex items-center gap-2">
              <input
                type="checkbox"
                class="hidden"
                value="house"
                v-model="category"
              />
              <span
                class="w-4 h-4 border-2 border-gray-400 rounded-md flex items-center justify-center checkbox-box"
              ></span>
              <span>مسکن و ساختمان</span>
            </div>

            <span
              class="min-w-[26px] h-[26px] flex items-center justify-center text-white text-xs rounded-md"
              :class="
                category.includes('house') ? 'bg-[#ff2c6d]' : 'bg-[#1e2430]'
              "
            >
              ۱۲
            </span>
          </label>

          <!-- item -->
          <label class="flex justify-between items-center mt-3 text-sm">
            <div class="flex items-center gap-2">
              <input
                type="checkbox"
                class="hidden"
                value="health"
                v-model="category"
              />
              <span
                class="w-4 h-4 border-2 border-gray-400 rounded-md flex items-center justify-center checkbox-box"
              ></span>
              <span>بهداشت و درمان</span>
            </div>

            <span
              class="min-w-[26px] h-[26px] flex items-center justify-center text-white text-xs rounded-md"
              :class="
                category.includes('health') ? 'bg-[#ff2c6d]' : 'bg-[#1e2430]'
              "
            >
              ۲۳
            </span>
          </label>

          <!-- item -->
          <label class="flex justify-between items-center mt-3 text-sm">
            <div class="flex items-center gap-2">
              <input
                type="checkbox"
                class="hidden"
                value="industry"
                v-model="category"
              />
              <span
                class="w-4 h-4 border-2 border-gray-400 rounded-md flex items-center justify-center checkbox-box"
              ></span>
              <span>صنعتی و کارخانه</span>
            </div>

            <span
              class="min-w-[26px] h-[26px] flex items-center justify-center text-white text-xs rounded-md"
              :class="
                category.includes('industry') ? 'bg-[#ff2c6d]' : 'bg-[#1e2430]'
              "
            >
              ۴
            </span>
          </label>
        </div>
      </transition>
    </div>
  </aside>
</template>

<script setup>
import { ref, computed } from "vue";

/* props */
const props = defineProps({
  search: String,
  sort: String,
  category: Array,
  availableOnly: Boolean,
});

/* emit */
const emit = defineEmits([
  "update:search",
  "update:sort",
  "update:category",
  "update:availableOnly",
]);

/* local models */
const search = computed({
  get: () => props.search,
  set: (val) => emit("update:search", val),
});

const sort = computed({
  get: () => props.sort,
  set: (val) => emit("update:sort", val),
});

const category = computed({
  get: () => props.category,
  set: (val) => emit("update:category", val),
});

const availableOnly = computed({
  get: () => props.availableOnly,
  set: (val) => emit("update:availableOnly", val),
});

const sortOpen = ref(true);
const categoryOpen = ref(true);
</script>

<style scoped>
/* radio checked dot */
.radio-dot::after {
  content: "";
  position: absolute;
  width: 8px;
  height: 8px;
  background: #ff2c6d;
  border-radius: 9999px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
}
input:checked + .radio-dot::after {
  opacity: 1;
}

/* checkbox tick */
.checkbox-box::after {
  content: "✓";
  font-size: 11px;
  color: white;
  display: none;
}
input:checked + .checkbox-box {
  background: #ff2c6d;
}
input:checked + .checkbox-box::after {
  display: block;
}
</style>
