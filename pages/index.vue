<template>
  <div dir="rtl" class="min-h-screen flex flex-col bg-[#f5f6fa]">
    <Header />

    <div class="max-w-[1300px] mx-auto w-full p-6 flex-1">
      <div
        dir="rtl"
        class="grid grid-cols-1 md:grid-cols-[220px_minmax(0,1fr)] lg:grid-cols-[260px_minmax(0,1fr)] gap-6"
      >
        <!-- sidebar -->
        <aside dir="rtl" class="h-fit md:sticky md:top-5">
          <SidebarFilter
            v-model:search="search"
            v-model:sort="sort"
            v-model:category="category"
            v-model:availableOnly="availableOnly"
          />
        </aside>
        <!-- content -->
        <main dir="rtl" class="flex flex-col min-w-0 overflow-hidden">
          <!-- topbar -->
          <div
            class="flex flex-col md:flex-row md:items-center md:justify-between bg-white rounded-2xl px-5 py-3 mb-6 gap-3"
          >
            <span class="text-sm text-[#333]"> فیلترهای اعمال شده </span>

            <div class="flex gap-2 flex-wrap">
              <!-- سرچ -->
              <span
                v-if="search"
                @click="search = ''"
                class="flex items-center gap-1 text-xs px-3 py-1.5 rounded-full bg-[#ffe8f0] text-[#ff2c6d] cursor-pointer transition hover:bg-[#ff2c6d] hover:text-white"
              >
                <font-awesome-icon
                  icon="magnifying-glass"
                  class="w-3.5 h-3.5"
                />
                <span>{{ search }}</span>
                <span class="mr-auto text-sm">✕</span>
              </span>

              <!-- دسته‌ها -->
              <span
                v-for="cat in category"
                :key="cat"
                @click="removeCategory(cat)"
                class="flex items-center gap-1 text-xs px-3 py-1.5 rounded-full bg-[#ffe8f0] text-[#ff2c6d] cursor-pointer transition hover:bg-[#ff2c6d] hover:text-white"
              >
                <font-awesome-icon
                  :icon="getCategoryIcon(cat)"
                  class="w-3.5 h-3.5"
                />
                <span>{{ getCategoryName(cat) }}</span>
                <span class="mr-auto text-sm">✕</span>
              </span>

              <!-- فقط موجود -->
              <span
                v-if="availableOnly"
                @click="availableOnly = false"
                class="flex items-center gap-1 text-xs px-3 py-1.5 rounded-full bg-[#ffe8f0] text-[#ff2c6d] cursor-pointer transition hover:bg-[#ff2c6d] hover:text-white"
              >
                <font-awesome-icon icon="check-circle" class="w-3.5 h-3.5" />
                <span>درب های موجود</span>
                <span class="mr-auto text-sm">✕</span>
              </span>
            </div>
          </div>

          <!-- loading -->
          <div v-if="pending" class="text-center py-16 text-gray-500">
            در حال دریافت محصولات...
          </div>

          <!-- empty -->
          <div
            v-else-if="!filteredProducts.length"
            class="text-center py-16 text-gray-500"
          >
            محصولی یافت نشد
          </div>

          <!-- products -->
          <div
            v-else
            class="grid gap-6 grid-cols-1 md:grid-cols-2 xl:grid-cols-3"
          >
            <ProductCard
              v-for="item in filteredProducts"
              :key="item.id"
              :product="item"
            />
          </div>
        </main>
      </div>
    </div>

    <Footer />
  </div>
</template>

<script setup>
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";
import ProductCard from "~/components/ProductCard.vue";
import SidebarFilter from "~/components/SidebarFilter.vue";

/* دریافت محصولات */
const { data: products, pending } = await useAsyncData(
  "products-list",
  async () => {
    const res = await $fetch("/api/products");

    return res.map((item, index) => ({
      id: item.id,
      title: `درب ${
        index % 2 === 0 ? "دو لنگه" : "تک لنگه"
      } مدل ${item.title.slice(0, 12)}`,
      image: item.image,
      price: item.price * 100000,
      category: item.category,
      available: item.available,
      rating: item.rating,
      count: item.count,
    }));
  },
  { server: true, default: () => [] },
);

/* فیلترها */
const search = ref("");
const sort = ref("");
const category = ref([]);
const availableOnly = ref(false);

/* فیلتر + سرچ + مرتب سازی */
const filteredProducts = computed(() => {
  let result = [...products.value];

  if (availableOnly.value) {
    result = result.filter((p) => p.available);
  }

  if (search.value) {
    result = result.filter((p) =>
      p.title.toLowerCase().includes(search.value.toLowerCase()),
    );
  }

  if (category.value.length) {
    result = result.filter((p) => category.value.includes(p.category));
  }

  if (sort.value === "low") result.sort((a, b) => a.count - b.count);
  if (sort.value === "high") result.sort((a, b) => b.count - a.count);
  if (sort.value === "rankHigh") result.sort((a, b) => b.rating - a.rating);
  if (sort.value === "rankLow") result.sort((a, b) => a.rating - b.rating);

  return result;
});

/* حذف دسته */
const removeCategory = (cat) => {
  category.value = category.value.filter((c) => c !== cat);
};

/* نام دسته */
const getCategoryName = (cat) => {
  switch (cat) {
    case "house":
      return "مسکن و ساختمان";
    case "industry":
      return "صنعتی و کارخانه";
    case "health":
      return "بهداشت و درمان";
    default:
      return cat;
  }
};

/* آیکون‌ها */
const getCategoryIcon = (cat) => {
  switch (cat) {
    case "house":
      return "house";
    case "industry":
      return "industry";
    case "health":
      return "hospital";
    default:
      return "tag";
  }
};
</script>
