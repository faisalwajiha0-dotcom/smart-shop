<template>
  <UMain>
    <!-- Hero Section -->
    <section
      class="relative overflow-hidden border-b border-gray-800 bg-[#0b1224]">
      <UContainer class="py-12 sm:py-16">
        <div class="grid items-center gap-8 lg:grid-cols-2">
          <!-- Left Content -->
          <div>
            <p
              class="mb-3 text-sm font-bold uppercase tracking-widest text-blue-400">
              Welcome to Smart Shop 🛍️
            </p>

            <h1
              class="text-4xl font-bold leading-tight text-white sm:text-5xl lg:text-6xl">
              Shop Smart.
              <span
                class="bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-transparent">
                Live Better.
              </span>
            </h1>

            <p
              class="mt-5 max-w-xl text-base leading-7 text-gray-400 sm:text-lg">
              Discover the latest electronics, fashion and accessories
              all in one place. Quality products with a simple shopping
              experience.
            </p>

            <!-- Buttons -->
            <div class="mt-6 flex flex-wrap gap-4">
              <UButton
                to="/products"
                size="lg"
                class="bg-blue-600 hover:bg-blue-700">
                Shop Now 🛒
              </UButton>

              <UButton
                to="/about"
                size="lg"
                variant="outline">
                Learn More
              </UButton>
            </div>
          </div>

          <!-- Right Image -->
          <div class="flex justify-center">
            <img
              src="https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?auto=format&fit=crop&w=900&q=80"
              alt="Smart shopping"
              class="w-full max-w-lg rounded-3xl object-cover shadow-2xl">
          </div>
        </div>
      </UContainer>
    </section>

    <!-- Categories Section -->
    <section class="bg-[#0f172a] py-14 sm:py-16">
      <UContainer>
        <div class="mb-8 text-center">
          <p
            class="text-sm font-semibold uppercase tracking-widest text-blue-400">
            Explore
          </p>

          <h2 class="mt-2 text-3xl font-bold text-white sm:text-4xl">
            Shop by Category
          </h2>

          <p class="mx-auto mt-3 max-w-2xl text-gray-400">
            Find everything you need from our popular categories.
          </p>
        </div>

        <div class="grid gap-5 sm:grid-cols-2 lg:grid-cols-4">
          <!-- Electronics -->
          <UCard
            class="cursor-pointer border-gray-800 bg-[#111827] transition hover:-translate-y-1 hover:border-blue-500">
            <div class="text-center">
              <div class="text-5xl">
                💻
              </div>

              <h3 class="mt-3 text-xl font-semibold text-white">
                Electronics
              </h3>

              <p class="mt-2 text-sm text-gray-400">
                Laptops, headphones and gadgets
              </p>
            </div>
          </UCard>

          <!-- Fashion -->
          <UCard
            class="cursor-pointer border-gray-800 bg-[#111827] transition hover:-translate-y-1 hover:border-purple-500">
            <div class="text-center">
              <div class="text-5xl">
                👕
              </div>

              <h3 class="mt-3 text-xl font-semibold text-white">
                Fashion
              </h3>

              <p class="mt-2 text-sm text-gray-400">
                Modern clothes and accessories
              </p>
            </div>
          </UCard>

          <!-- Footwear -->
          <UCard
            class="cursor-pointer border-gray-800 bg-[#111827] transition hover:-translate-y-1 hover:border-blue-500">
            <div class="text-center">
              <div class="text-5xl">
                👟
              </div>

              <h3 class="mt-3 text-xl font-semibold text-white">
                Footwear
              </h3>

              <p class="mt-2 text-sm text-gray-400">
                Comfortable shoes and sneakers
              </p>
            </div>
          </UCard>

          <!-- Accessories -->
          <UCard
            class="cursor-pointer border-gray-800 bg-[#111827] transition hover:-translate-y-1 hover:border-purple-500">
            <div class="text-center">
              <div class="text-5xl">
                🎧
              </div>

              <h3 class="mt-3 text-xl font-semibold text-white">
                Accessories
              </h3>

              <p class="mt-2 text-sm text-gray-400">
                Smart accessories for everyday use
              </p>
            </div>
          </UCard>
        </div>
      </UContainer>
    </section>

    <!-- Featured Products -->
    <section class="bg-[#0b1224] py-20">
      <UContainer>
        <!-- Center Heading -->
        <div class="mb-12 text-center">
          <p
            class="text-sm font-semibold uppercase tracking-widest text-purple-400">
            Our Collection
          </p>

          <h2 class="mt-2 text-4xl font-bold text-white">
            Featured Products
          </h2>

          <p class="mx-auto mt-4 max-w-2xl text-gray-400">
            Check out some of our popular products and find something perfect for you.
          </p>
        </div>

        <!-- Product Cards -->
        <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
          <!-- Product 1 -->
          <UCard class="overflow-hidden border-gray-800 bg-[#111827]">
            <img
              src="https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=800&q=80"
              alt="Wireless Headphones"
              class="h-56 w-full object-cover">

            <div class="p-5">
              <p class="text-sm text-blue-400">
                Electronics
              </p>

              <h3 class="mt-2 text-xl font-semibold text-white">
                Wireless Headphones
              </h3>

              <p class="mt-2 text-gray-400">
                High quality wireless headphones.
              </p>

              <div class="mt-5 flex items-center justify-between">
                <span class="text-xl font-bold text-white">
                  $49.99
                </span>

                <UButton
                  to="/products"
                  size="sm">
                  View Product
                </UButton>
              </div>
            </div>
          </UCard>

          <!-- Product 2 -->
          <UCard class="overflow-hidden border-gray-800 bg-[#111827]">
            <img
              src="https://images.unsplash.com/photo-1523275335684-37898b6baf30?auto=format&fit=crop&w=800&q=80"
              alt="Smart Watch"
              class="h-56 w-full object-cover">

            <div class="p-5">
              <p class="text-sm text-purple-400">
                Accessories
              </p>

              <h3 class="mt-2 text-xl font-semibold text-white">
                Smart Watch
              </h3>

              <p class="mt-2 text-gray-400">
                Stay connected with a modern smart watch.
              </p>

              <div class="mt-5 flex items-center justify-between">
                <span class="text-xl font-bold text-white">
                  $79.99
                </span>

                <UButton
                  to="/products"
                  size="sm">
                  View Product
                </UButton>
              </div>
            </div>
          </UCard>

          <!-- Product 3 -->
          <UCard class="overflow-hidden border-gray-800 bg-[#111827]">
            <img
              src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=800&q=80"
              alt="Classic Sneakers"
              class="h-56 w-full object-cover">

            <div class="p-5">
              <p class="text-sm text-blue-400">
                Footwear
              </p>

              <h3 class="mt-2 text-xl font-semibold text-white">
                Classic Sneakers
              </h3>

              <p class="mt-2 text-gray-400">
                Comfortable sneakers for everyday style.
              </p>

              <div class="mt-5 flex items-center justify-between">
                <span class="text-xl font-bold text-white">
                  $59.99
                </span>

                <UButton
                  to="/products"
                  size="sm">
                  View Product
                </UButton>
              </div>
            </div>
          </UCard>
        </div>

        <!-- View All Button -->
        <div class="mt-10 text-center">
          <UButton
            to="/products"
            variant="outline"
            size="lg">
            View All Products →
          </UButton>
        </div>
      </UContainer>
    </section>

    <!-- CTA Section -->
    <section class="bg-[#0f172a] py-14 sm:py-16">
      <UContainer>
        <div
          class="rounded-3xl border border-gray-800 bg-linear-to-r from-blue-600/20 to-purple-600/20 px-6 py-12 text-center">
          <h2 class="text-3xl font-bold text-white sm:text-4xl">
            Ready to Start Shopping?
          </h2>

          <p class="mx-auto mt-4 max-w-2xl text-gray-400">
            Explore our products and find something perfect for you.
          </p>

          <UButton
            to="/products"
            size="lg"
            class="mt-7 bg-blue-600 hover:bg-blue-700">
            Explore Products 🛍️
          </UButton>
        </div>
      </UContainer>
    </section>
  </UMain>
</template>
