<template>
  <div
    dir="rtl"
    class="min-h-screen flex flex-col overflow-x-hidden bg-[#f1f3f8]"
  >
    <Header />

    <!-- breadcrumb -->
    <div
      class="w-[95%] max-w-[1500px] mx-auto py-4 px-2 text-[14px] text-[#7b808a] flex items-center gap-2 rtl"
    >
      <NuxtLink to="/" class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="18"
          height="18"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.8"
            d="M3 10.5L12 3l9 7.5M5 9.5V21h5v-6h4v6h5V9.5"
          />
        </svg>
      </NuxtLink>

      <span class="text-[#b7bcc8]">›</span>
      <NuxtLink to="/" class="text-[#7b8190] no-underline"
        >لیست محصولات</NuxtLink
      >
      <span class="text-[#b7bcc8]">›</span>
      <span class="text-[#3d5a80]">{{ product?.title }}</span>
    </div>

    <div class="w-full max-w-[1024px] mx-auto px-4 sm:px-6 py-5 flex-grow">
      <!-- loading -->
      <div v-if="pending" class="text-center py-16 text-[#666]">
        در حال دریافت اطلاعات محصول...
      </div>

      <!-- error -->
      <div v-else-if="error" class="text-center py-16 text-[#666]">
        خطا در دریافت محصول
      </div>

      <!-- content -->
      <div v-else class="flex flex-col gap-6 w-full">
        <!-- image card -->
        <div class="bg-white rounded-2xl p-6 w-full">
          <h1 class="text-[18px] mb-4 text-[#2e2e2e] font-bold">
            {{ product.title }}
          </h1>

          <div
            class="relative bg-[#eef1f6] rounded-xl flex items-center justify-center h-[350px] overflow-hidden sm:h-[300px]"
          >
            <img
              :src="product.image"
              class="w-full h-full object-cover"
              @click="openZoom"
            />

            <div
              class="absolute right-3 top-3 bg-black/45 backdrop-blur-md w-9 h-9 rounded-lg flex items-center justify-center cursor-pointer"
              @click="openZoom"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="18"
                height="18"
                viewBox="0 0 24 24"
                fill="none"
                stroke="#fff"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <circle cx="11" cy="11" r="7"></circle>
                <line x1="21" y1="21" x2="16.5" y2="16.5"></line>
              </svg>
            </div>
          </div>
        </div>

        <!-- zoom modal -->
        <div
          v-if="showZoom"
          class="fixed inset-0 bg-black/75 flex items-center justify-center z-[1000]"
          @click="closeZoom"
        >
          <img
            :src="product.image"
            class="max-w-[80%] max-h-[80%] rounded-xl bg-white p-5"
          />
        </div>

        <!-- specs -->
        <!-- specs -->
        <div class="bg-white rounded-2xl p-6 w-full mx-auto">
          <h2 class="text-[18px] mb-4 text-[#2f3a4b] font-bold">مشخصات فنی</h2>

          <div class="flex flex-col gap-2">
            <!-- price -->
            <div
              class="grid grid-cols-1 sm:grid-cols-[minmax(120px,220px)_1fr] rounded-xl overflow-hidden"
            >
              <div
                class="bg-[#eef1f6] p-3 text-right text-[#6b7280] text-[14px] sm:text-right"
              >
                قیمت
              </div>
              <div
                class="bg-[#f6f8fc] p-3 text-right text-[14px] text-[#2e2e2e]"
              >
                {{ formatPrice(product.price) }} تومان
              </div>
            </div>

            <!-- description -->
            <div
              class="grid grid-cols-1 sm:grid-cols-[minmax(120px,220px)_1fr] rounded-xl overflow-hidden"
            >
              <div
                class="bg-[#eef1f6] p-3 text-right text-[#6b7280] text-[14px] sm:text-right"
              >
                توضیحات
              </div>
              <div
                class="bg-[#f6f8fc] p-3 text-right text-[14px] text-[#2e2e2e]"
              >
                {{ product.description }}
              </div>
            </div>

            <!-- type -->
            <div
              class="grid grid-cols-1 sm:grid-cols-[minmax(120px,220px)_1fr] rounded-xl overflow-hidden"
            >
              <div
                class="bg-[#eef1f6] p-3 text-right text-[#6b7280] text-[14px] sm:text-right"
              >
                دسته بندی
              </div>
              <div
                class="bg-[#f6f8fc] p-3 text-right text-[14px] text-[#2e2e2e]"
              >
                {{ product.type }}
              </div>
            </div>

            <!-- rating -->
            <div
              class="grid grid-cols-1 sm:grid-cols-[minmax(120px,220px)_1fr] rounded-xl overflow-hidden"
            >
              <div
                class="bg-[#eef1f6] p-3 text-right text-[#6b7280] text-[14px] sm:text-right"
              >
                رتبه
              </div>
              <div
                class="bg-[#f6f8fc] p-3 text-right text-[14px] text-[#2e2e2e]"
              >
                {{ product.rating }}
              </div>
            </div>

            <!-- count -->
            <div
              class="grid grid-cols-1 sm:grid-cols-[minmax(120px,220px)_1fr] rounded-xl overflow-hidden"
            >
              <div
                class="bg-[#eef1f6] p-3 text-right text-[#6b7280] text-[14px] sm:text-right"
              >
                تعداد
              </div>
              <div
                class="bg-[#f6f8fc] p-3 text-right text-[14px] text-[#2e2e2e]"
              >
                {{ product.count }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <Footer />
  </div>
</template>

<script setup>
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";

const route = useRoute();
const id = route.params.id;

const {
  data: product,
  pending,
  error,
} = await useAsyncData("product-" + id, async () => {
  const products = await $fetch("/api/products");

  const found = products.find((p) => p.id == id);

  if (!found) {
    throw createError({
      statusCode: 404,
      statusMessage: "Product not found",
    });
  }

  return {
    ...found,
    price: found.price * 100000,
  };
});

const formatPrice = (price) => {
  return new Intl.NumberFormat("fa-IR").format(price);
};

const showZoom = ref(false);

const openZoom = () => {
  showZoom.value = true;
};

const closeZoom = () => {
  showZoom.value = false;
};
</script>
