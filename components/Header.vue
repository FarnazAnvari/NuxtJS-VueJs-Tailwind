<template>
  <header
    class="bg-white border-b border-gray-200 rounded-[10px] py-4 relative z-[2000]"
  >
    <div class="flex items-center justify-between rtl max-w-app mx-auto px-6">
      <!-- دکمه همبرگری (موبایل) -->
      <button
        class="block md:hidden bg-transparent border-none text-[20px] cursor-pointer"
        @click="menuOpen = !menuOpen"
      >
        <font-awesome-icon :icon="['fas', 'bars']" />
      </button>

      <!-- منو -->
      <nav
        :class="[
          'absolute md:static top-[70px] right-0 w-full bg-white flex-col items-start gap-4 p-5 md:flex md:flex-row md:items-center md:w-auto md:bg-transparent md:p-0 md:gap-6',
          menuOpen ? 'flex' : 'hidden',
        ]"
      >
        <NuxtLink
          to="/"
          class="no-underline text-[#1d1d1d] text-sm flex items-center gap-[6px] relative transition-colors duration-300 hover:text-[#ff2c6d]"
        >
          <font-awesome-icon :icon="['fas', 'list']" class="icon text-[14px]" />
          لیست محصولات
        </NuxtLink>

        <NuxtLink
          to="#"
          class="no-underline text-[#1d1d1d] text-sm flex items-center gap-[6px] relative transition-colors duration-300 hover:text-[#ff2c6d]"
          active-class="active-link"
        >
          <font-awesome-icon
            :icon="['fas', 'comments']"
            class="icon text-[14px]"
          />
          دریافت مشاوره
        </NuxtLink>

        <NuxtLink
          to="#"
          class="no-underline text-[#1d1d1d] text-sm flex items-center gap-[6px] relative transition-colors duration-300 hover:text-[#ff2c6d]"
          active-class="active-link"
        >
          <font-awesome-icon
            :icon="['fas', 'question-circle']"
            class="icon text-[14px]"
          />
          سوالات متداول
        </NuxtLink>

        <NuxtLink
          to="#"
          class="no-underline text-[#1d1d1d] text-sm flex items-center gap-[6px] relative transition-colors duration-300 hover:text-[#ff2c6d]"
          active-class="active-link"
        >
          <font-awesome-icon
            :icon="['fas', 'phone']"
            class="icon text-[14px]"
          />
          تماس با ما
        </NuxtLink>
      </nav>

      <!-- دکمه تماس -->
      <button
        class="bg-[#ff2c6d] text-white border-none px-[18px] py-2 rounded-full cursor-pointer flex items-center gap-2 text-sm"
      >
        تماس
        <font-awesome-icon :icon="['fas', 'phone']" class="text-[14px]" />
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";

const menuOpen = ref(false);
</script>

<style scoped>
/* حداکثر عرض مشابه 1100px */
.max-w-app {
  max-width: 1100px;
}

/* جهت RTL */
.rtl {
  direction: rtl;
}

/* لینک فعال (جایگزین .nav a.active و ::after) */
.active-link {
  color: #ff2c6d /* text color */;
}

.active-link .icon {
  color: #ff2c6d;
}

/* خط زیر لینک فعال */
.active-link::after {
  content: "";
  position: absolute;
  bottom: -6px;
  right: 0;
  width: 100%;
  height: 2px;
  background: #ff2c6d;
}

/* برای حذف underline پیش‌فرض NuxtLink در بعضی resetها */
.no-underline {
  text-decoration: none;
}
</style>
