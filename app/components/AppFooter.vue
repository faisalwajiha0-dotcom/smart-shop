<template>
  <footer
    class="bg-[#0f172a] text-white pt-8 pb-16 px-8 font-sans border-t border-gray-800/50">
    <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-4 gap-10">
      <!-- Brand -->
      <div class="space-y-4">
        <h2
          class="text-4xl font-bold bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent">
          Smart Shop
        </h2>

        <p class="text-gray-300 text-sm leading-relaxed max-w-xs">
          Your trusted destination for quality products and a smooth,
          modern online shopping experience.
        </p>

        <!-- Social Icons -->
        <div class="flex gap-4 pt-2">
          <a
            href="#"
            class="hover:text-blue-400 transition duration-300"
            aria-label="Facebook">
            <i class="fab fa-facebook text-lg" />
          </a>

          <a
            href="#"
            class="hover:text-pink-400 transition duration-300"
            aria-label="Instagram">
            <i class="fab fa-instagram text-lg" />
          </a>

          <a
            href="#"
            class="hover:text-blue-300 transition duration-300"
            aria-label="Twitter">
            <i class="fab fa-twitter text-lg" />
          </a>
        </div>
      </div>

      <!-- Shop -->
      <div>
        <h3
          class="bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent font-bold text-xl mb-6 w-fit">
          Shop
        </h3>

        <ul class="space-y-3 text-gray-300 text-sm">
          <li>
            <NuxtLink
              to="/products"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              All Products
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/products"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              Categories
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/products"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              Featured Products
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/products"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              New Arrivals
            </NuxtLink>
          </li>
        </ul>
      </div>

      <!-- Shopping -->
      <div>
        <h3
          class="bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent font-bold text-xl mb-6 w-fit">
          Shopping
        </h3>

        <ul class="space-y-3 text-gray-300 text-sm">
          <li>
            <NuxtLink
              to="/cart"
              class="hover:text-purple-400 hover:pl-2 transition-all duration-300">
              Shopping Cart
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/checkout"
              class="hover:text-purple-400 hover:pl-2 transition-all duration-300">
              Checkout
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/about"
              class="hover:text-purple-400 hover:pl-2 transition-all duration-300">
              About Smart Shop
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/contact"
              class="hover:text-purple-400 hover:pl-2 transition-all duration-300">
              Contact Us
            </NuxtLink>
          </li>
        </ul>
      </div>

      <!-- Quick Links -->
      <div>
        <h3
          class="bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent font-bold text-xl mb-6 w-fit">
          Quick Links
        </h3>

        <ul class="space-y-3 text-gray-300 text-sm">
          <li>
            <NuxtLink
              to="/"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              Home
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/products"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              Shop Now
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/about"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              About Us
            </NuxtLink>
          </li>

          <li>
            <NuxtLink
              to="/contact"
              class="hover:text-blue-400 hover:pl-2 transition-all duration-300">
              Help & Contact
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>

    <!-- Bottom -->
    <div
      class="max-w-7xl mx-auto mt-10 pt-6 border-t border-gray-800/60 text-center">
      <p class="text-gray-500 text-sm tracking-wide">
        © 2026
        <span class="text-blue-400 font-semibold">Smart Shop</span>
        | All Rights Reserved
      </p>
    </div>
  </footer>
</template>
