<template>
  <!-- TOP -->
  <div class="bg-white border-t border-gray-200 py-16 rtl">
    <div class="max-w-[1200px] mx-auto px-6 lg:pr-24 lg:pl-16">
      <div
        class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-[minmax(260px,1.4fr)_1fr_1fr_1fr] gap-8 lg:gap-20 items-start"
      >
        <!-- support -->
        <div
          class="text-gray-500 text-sm leading-8 pt-0 lg:pt-[125px] text-center lg:text-right sm:col-span-2 lg:col-span-1 lg:whitespace-nowrap"
        >
          هفت روز هفته از ۸ صبح تا ۱۲ شب پاسخگو هستیم
        </div>

        <!-- col 1 -->
        <div
          class="flex flex-col gap-2 text-center sm:text-right items-center sm:items-start"
        >
          <h3 class="text-lg font-bold text-gray-800 mb-3">دسترسی سریع</h3>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            درباره ما
          </a>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            بلاگ
          </a>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            تماس با ما
          </a>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            خدمات پس از فروش
          </a>
        </div>

        <!-- col 2 -->
        <div
          class="flex flex-col gap-2 text-center sm:text-right items-center sm:items-start"
        >
          <h3 class="text-lg font-bold text-gray-800 mb-3">راهنمای سایت</h3>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            قوانین و مقررات
          </a>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            دریافت مشاوره
          </a>

          <a
            href="#"
            class="text-sm text-gray-500 transition-all duration-300 hover:text-[#ff2e63] hover:-translate-x-1"
          >
            انتقادات و پیشنهادات
          </a>
        </div>

        <!-- col 3 Social Icons -->
        <div
          class="flex flex-col gap-2 text-center sm:text-right items-center sm:items-start"
        >
          <h3 class="text-lg font-bold text-gray-800 mb-3">شبکه‌های اجتماعی</h3>

          <!-- Telegram -->
          <a
            href="#"
            class="group inline-flex items-center gap-3 justify-center sm:justify-start transform transition-transform duration-300 ease-out will-change-transform hover:scale-[1.05]"
          >
            <div
              class="w-9 h-9 rounded-full bg-[#eef1f6] text-gray-600 flex items-center justify-center text-base transition-colors duration-300 group-hover:bg-[#ff2e63] group-hover:text-white"
            >
              <font-awesome-icon :icon="['fab', 'telegram']" />
            </div>

            <span
              class="text-gray-600 transition-colors duration-300 group-hover:text-[#ff2e63]"
            >
              تلگرام
            </span>
          </a>

          <!-- Instagram -->
          <a
            href="#"
            class="group inline-flex items-center gap-3 justify-center sm:justify-start transform transition-transform duration-300 ease-out will-change-transform hover:scale-[1.05]"
          >
            <div
              class="w-9 h-9 rounded-full bg-[#eef1f6] text-gray-600 flex items-center justify-center text-base transition-colors duration-300 group-hover:bg-[#ff2e63] group-hover:text-white"
            >
              <font-awesome-icon :icon="['fab', 'instagram']" />
            </div>

            <span
              class="text-gray-600 transition-colors duration-300 group-hover:text-[#ff2e63]"
            >
              اینستاگرام
            </span>
          </a>

          <!-- LinkedIn -->
          <a
            href="#"
            class="group inline-flex items-center gap-3 justify-center sm:justify-start transform transition-transform duration-300 ease-out will-change-transform hover:scale-[1.05]"
          >
            <div
              class="w-9 h-9 rounded-full bg-[#eef1f6] text-gray-600 flex items-center justify-center text-base transition-colors duration-300 group-hover:bg-[#ff2e63] group-hover:text-white"
            >
              <font-awesome-icon :icon="['fab', 'linkedin']" />
            </div>

            <span
              class="text-gray-600 transition-colors duration-300 group-hover:text-[#ff2e63]"
            >
              لینکدین
            </span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- BOTTOM -->
  <div class="bg-[#f6f6f6] py-9 rtl">
    <div
      class="max-w-[1200px] mx-auto px-6 flex flex-col lg:flex-row justify-center lg:justify-between items-center gap-5 text-center"
    >
      <div class="flex-1 w-full max-w-lg lg:max-w-none">
        <p class="text-xs text-gray-500 mb-4 leading-7">
          تمامی حقوق مادی و معنوی این وبسایت متعلق به میباشد و هر گونه کپی
          برداری پیگرد قانونی دارد
        </p>

        <div class="flex justify-center gap-3 flex-wrap">
          <a
            class="w-10 h-10 rounded-full bg-[#ff2e63] flex items-center justify-center text-white text-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-lg"
          >
            <font-awesome-icon :icon="['fab', 'linkedin']" />
          </a>

          <a
            class="w-10 h-10 rounded-full bg-[#ff2e63] flex items-center justify-center text-white text-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-lg"
          >
            <font-awesome-icon :icon="['fab', 'youtube']" />
          </a>

          <a
            class="w-10 h-10 rounded-full bg-[#ff2e63] flex items-center justify-center text-white text-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-lg"
          >
            <font-awesome-icon :icon="['fab', 'twitter']" />
          </a>

          <a
            class="w-10 h-10 rounded-full bg-[#ff2e63] flex items-center justify-center text-white text-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-lg"
          >
            <font-awesome-icon :icon="['fab', 'instagram']" />
          </a>

          <a
            class="w-10 h-10 rounded-full bg-[#ff2e63] flex items-center justify-center text-white text-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-lg"
          >
            <font-awesome-icon :icon="['fab', 'telegram']" />
          </a>
        </div>
      </div>

      <div class="flex gap-4 justify-center lg:translate-x-24">
        <img
          src="/images/samandehi.png"
          class="w-16 bg-white p-2 rounded-md shadow"
          alt="samandehi"
        />
        <img
          src="/images/enamad.png"
          class="w-16 bg-white p-2 rounded-md shadow"
          alt="enamad"
        />
      </div>
    </div>
  </div>
</template>
