<script setup>
const products = [
  {
    id: 1,
    title: 'Wireless Headphones',
    category: 'Electronics',
    price: 49.99,
    rating: 4.8,
    image:
      'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 2,
    title: 'Smart Watch',
    category: 'Accessories',
    price: 79.99,
    rating: 4.7,
    image:
      'https://images.unsplash.com/photo-1523275335684-37898b6baf30?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 3,
    title: 'Classic Sneakers',
    category: 'Footwear',
    price: 59.99,
    rating: 4.6,
    image:
      'https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 4,
    title: 'Casual T-Shirt',
    category: 'Fashion',
    price: 29.99,
    rating: 4.5,
    image:
      'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 5,
    title: 'Laptop',
    category: 'Electronics',
    price: 799.99,
    rating: 4.9,
    image:
      'https://images.unsplash.com/photo-1496181133206-80ce9b88a853?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 6,
    title: 'Backpack',
    category: 'Accessories',
    price: 39.99,
    rating: 4.4,
    image:
      'https://images.unsplash.com/photo-1553062407-98eeb64c6a62?auto=format&fit=crop&w=800&q=80'
  }
]

const search = ref('')
const selectedCategory = ref('All')
const sortBy = ref('default')

const categories = [
  'All',
  'Electronics',
  'Fashion',
  'Footwear',
  'Accessories'
]

const filteredProducts = computed(() => {
  const result = products.filter(product => {
    const matchesSearch = product.title
      .toLowerCase()
      .includes(search.value.toLowerCase())

    const matchesCategory
      = selectedCategory.value === 'All'
        || product.category === selectedCategory.value

    return matchesSearch && matchesCategory
  })

  if (sortBy.value === 'low') {
    result.sort((a, b) => a.price - b.price)
  }

  if (sortBy.value === 'high') {
    result.sort((a, b) => b.price - a.price)
  }

  if (sortBy.value === 'name') {
    result.sort((a, b) => a.title.localeCompare(b.title))
  }

  return result
})
</script>

<template>
  <UMain class="min-h-screen">
    <!-- Page Header -->
    <section class="border-b border-gray-800">
      <UContainer class="py-14 text-center sm:py-16">
        <h1
          class="mt-0  text-5xl font-bold text-blue-500">
          Products
        </h1>
        <p
          class="text-sm mt-4 font-bold uppercase tracking-[0.25em] text-purple-400">
          Our Collection
        </p>

        <p class="mx-auto mt-4 max-w-2xl text-purple-200 sm:text-lg">
          Explore our collection of quality products and find something
          perfect for you.
        </p>
      </UContainer>
    </section>

    <!-- Filters -->
    <section class="border-b border-gray-800 bg-[#0f172a]">
      <UContainer class="py-7">
        <div class="grid gap-4 md:grid-cols-3">
          <!-- Search -->
          <UInput
            v-model="search"
            size="lg"
            placeholder="Search products..."
            icon="i-lucide-search" />

          <!-- Category -->
          <USelect
            v-model="selectedCategory"
            :items="categories"
            size="lg" />

          <!-- Sort -->
          <USelect
            v-model="sortBy"
            :items="[
              { label: 'Sort By', value: 'default' },
              { label: 'Price: Low to High', value: 'low' },
              { label: 'Price: High to Low', value: 'high' },
              { label: 'Name: A to Z', value: 'name' },
            ]"
            size="lg" />
        </div>
      </UContainer>
    </section>

    <!-- Products Section -->
    <section class="py-14 sm:py-16">
      <UContainer>
        <!-- Section Heading -->
        <div class="mb-10 text-center">
          <p
            class="text-sm font-semibold uppercase tracking-[0.25em] text-purple-400">
            Discover
          </p>

          <h2
            class="mt-2 bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-5xl font-bold text-transparent ">
            All Products
          </h2>

          <p class="mt-3 text-gray-400">
            {{ filteredProducts.length }} products available
          </p>
        </div>
        <!-- Product Grid -->
        <div
          v-if="filteredProducts.length"
          class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
          <!-- Product Card -->
          <UCard
            v-for="product in filteredProducts"
            :key="product.id"
            class="group flex h-full min-h-125 flex-col overflow-hidden border border-gray-800 bg-[#111827] transition-all duration-300 hover:-translate-y-2 hover:border-purple-500 hover:shadow-xl hover:shadow-purple-500/10">
            <!-- Product Image -->
            <div class="relative h-60 w-full overflow-hidden bg-[#0f172a]">
              <img
                :src="product.image"
                :alt="product.title"
                class="h-full w-full object-cover transition duration-500 group-hover:scale-110">

              <!-- Category -->
              <span
                class="absolute left-4 top-4 rounded-full border border-blue-400/30 bg-[#0b1224]/90 px-3 py-1 text-xs font-semibold text-blue-400 backdrop-blur">
                {{ product.category }}
              </span>
            </div>

            <!-- Product Content -->
            <div class="flex flex-1 flex-col p-5">
              <!-- Title + Rating -->
              <div class="flex items-center justify-between gap-3">
                <h3
                  class="text-lg font-bold text-white transition group-hover:text-blue-400">
                  {{ product.title }}
                </h3>

                <span class="shrink-0 text-sm text-yellow-400">
                  ⭐ {{ product.rating }}
                </span>
              </div>

              <!-- Description -->
              <p class="mt-3 min-h-12 text-sm leading-6 text-gray-400">
                Quality product with a modern design and great value.
              </p>

              <!-- Bottom -->
              <div
                class="mt-auto flex items-center justify-between gap-3 border-t border-gray-800 pt-5">
                <!-- Price -->
                <span
                  class="bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-xl font-extrabold text-transparent">
                  ${{ product.price }}
                </span>

                <!-- Button -->
                <UButton
                  :to="`/products/${product.id}`"
                  size="sm"
                  class="bg-linear-to-r from-blue-600 to-purple-600 text-white transition hover:from-blue-500 hover:to-purple-500">
                  View Details
                </UButton>
              </div>
            </div>
          </UCard>
        </div>

        <!-- No Products -->
        <div
          v-else
          class="py-20 text-center">
          <div class="text-5xl">
            🔍
          </div>

          <h3 class="mt-4 text-2xl font-bold text-white">
            No Products Found
          </h3>

          <p class="mt-2 text-gray-400">
            Try another search or category.
          </p>
        </div>
      </UContainer>
    </section>
  </UMain>
</template>
