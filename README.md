# 🛍️ Nuxt Shop

A modern e-commerce product listing built with **Nuxt 3, Vue 3, and TailwindCSS**.  
This project features SSR, advanced product filtering, sorting, a responsive UI, and an internal API—all fully optimized for RTL and Persian language.

---

## 🚀 Tech Stack

- **Nuxt 3** (Vue 3, Composition API)
- **TailwindCSS 4**
- **FontAwesome 7**
- Built-in **API layer** (`/api/products`)
- SSR (Server-Side Rendering)
- RTL and Persian support

---

## ✨ Features

### 🏪 Product Listing Page

- Fetches product data from Nuxt server API
- Filter by:
  - Search term
  - Category
  - "In stock only"
- Sort by:
  - Quantity (low/high)
  - Rating (low/high)
- Display active filters as tags
- Responsive grid for product cards

### 📄 Product Details Page

- Dynamic routing (`/products/[id]`)
- SSR data fetching and 404 handling
- Technical specifications: price, description, category, rating, quantity
- Clean price formatting (fa-IR locale)
- Product image zoom modal
- Breadcrumb navigation

### 🎨 Modern UI

- Fully responsive (mobile-first)
- RTL support for Persian layout
- Sticky filter sidebar on desktop
- Elegant, clean design with TailwindCSS
- FontAwesome icon integration

---

## 📁 Folder Structure

```text
nuxt-shop/
├── assets/
│   └── css/
│       └── tailwind.css
├── components/
│   ├── Header.vue
│   ├── Footer.vue
│   ├── ProductCard.vue
│   └── SidebarFilter.vue
├── composables/
│   └── useProducts.js
├── pages/
│   ├── index.vue
│   └── products/
│       └── [id].vue
├── server/
│   └── api/
│       └── products.js
├── public/
│   └── images/
├── nuxt.config.ts
├── tailwind.config.ts
├── package.json
└── README.md
```

# 🛍️ فروشگاه Nuxt Shop

یک پروژه فروشگاهی مدرن ساخته‌شده با **Nuxt 3، Vue 3 و TailwindCSS**.  
این پروژه شامل لیست محصولات، فیلتر و مرتب‌سازی پیشرفته، UI واکنش‌گرا، صفحه جزئیات محصول و API داخلی است.  
همچنین به صورت **SSR** پیاده‌سازی شده و پشتیبانی کامل از **راست‌به‌چپ (RTL)** و زبان فارسی دارد.

---

## 🚀 تکنولوژی‌های استفاده شده

- **Nuxt 3** (با Vue 3 و Composition API)
- **TailwindCSS 4**
- **FontAwesome 7**
- **API داخلی** با مسیر `/api/products`
- **SSR (رندر سمت سرور)**
- پشتیبانی کامل RTL و فارسی

---

## ✨ قابلیت‌ها

### 🏪 صفحه لیست محصولات

- دریافت داده‌ها از API داخلی
- فیلتر بر اساس:
  - عبارت جستجو
  - دسته‌بندی
  - فقط محصولات موجود
- مرتب‌سازی بر اساس:
  - تعداد (کم → زیاد | زیاد → کم)
  - رتبه (کم → زیاد | زیاد → کم)
- نمایش تگ‌های فیلتر فعال
- گرید واکنش‌گرا برای کارت محصول

---

### 📄 صفحه جزئیات محصول

- مسیر داینامیک:
- دریافت اطلاعات محصول با SSR
- نمایش اطلاعات فنی محصول:
  - قیمت
  - توضیحات
  - دسته‌بندی
  - امتیاز
  - تعداد موجود
- فرمت قیمت به صورت فارسی (fa-IR)
- مودال بزرگ‌نمایی تصویر محصول
- مسیریابی Breadcrumb

---

### 🎨 رابط کاربری (UI)

- کاملاً واکنش‌گرا (Mobile-first)
- پشتیبانی کامل از RTL
- سایدبار فیلتر چسبنده (sticky) در دسکتاپ
- طراحی تمیز و مدرن با TailwindCSS
- آیکون‌های FontAwesome

---

## 📁 ساختار پوشه‌ها

```text
nuxt-shop/
├── assets/
│   └── css/
│       └── tailwind.css
├── components/
│   ├── Header.vue
│   ├── Footer.vue
│   ├── ProductCard.vue
│   └── SidebarFilter.vue
├── composables/
│   └── useProducts.js
├── pages/
│   ├── index.vue
│   └── products/
│       └── [id].vue
├── server/
│   └── api/
│       └── products.js
├── public/
│   └── images/
├── nuxt.config.ts
├── tailwind.config.ts
├── package.json
└── README.md
```
