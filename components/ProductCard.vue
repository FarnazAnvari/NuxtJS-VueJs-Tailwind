<template>
  <NuxtLink
    :to="`/products/${product.id}`"
    class="relative flex flex-col bg-white rounded-[20px] overflow-hidden p-[18px] text-inherit no-underline transition-all duration-300 ease-in-out shadow-[0_8px_25px_rgba(0,0,0,0.06)] min-w-0 hover:-translate-y-[6px] hover:shadow-[0_16px_40px_rgba(0,0,0,0.1)]"
  >
    <!-- category badge -->
    <div
      class="absolute top-[14px] right-[14px] bg-[#f2f4ff] text-[#5563ff] text-[11px] px-[10px] py-[5px] rounded-[10px]"
    >
      {{ categoryName }}
    </div>

    <!-- image -->
    <div
      class="h-[170px] flex items-center justify-center mb-[14px] max-[1024px]:h-[140px]"
    >
      <img
        :src="product.image"
        class="max-h-[160px] object-contain transition-transform duration-[350ms] ease-in-out hover:scale-[1.08] max-[1024px]:max-h-[130px]"
      />
    </div>

    <!-- body -->
    <div class="flex flex-col flex-grow">
      <h3
        class="text-[14px] leading-[1.8] text-[#333333] mb-[10px] line-clamp-2"
      >
        {{ product.title }}
      </h3>

      <p class="text-[15px] font-semibold text-[#111010] mb-[14px]">
        {{ formatPrice(product.price) }} تومان
      </p>

      <div
        class="mt-auto border border-[#ff2c6d] text-[#ff2c6d] text-center py-[9px] rounded-[12px] text-[13px] transition-all duration-200 ease-in-out hover:bg-[#ff2c6d] hover:text-white"
      >
        مشاهده جزئیات
      </div>
    </div>
  </NuxtLink>
</template>

<script setup>
const props = defineProps({
  product: Object,
});

const formatPrice = (price) => {
  return new Intl.NumberFormat("fa-IR").format(price);
};

const categoryMap = {
  house: "مسکن و ساختمان",
  industry: "صنعتی و کارخانه",
  health: "بهداشت و درمان",
};

const categoryName = categoryMap[props.product.category] || "";
</script>
