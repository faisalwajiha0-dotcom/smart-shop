<script setup>
import { ref, computed, onMounted } from 'vue'
import { useToast } from '#imports'

const toast = useToast()

const cart = ref([])

/* =========================
   LOAD CART FROM LOCALSTORAGE
========================= */
onMounted(() => {
  const savedCart = localStorage.getItem('cart')

  if (savedCart) {
    try {
      cart.value = JSON.parse(savedCart)
    }
    catch {
      cart.value = []
    }
  }
})

/* =========================
   SAVE CART
========================= */
const saveCart = () => {
  localStorage.setItem('cart', JSON.stringify(cart.value))
}

/* =========================
   TOTAL ITEMS
========================= */
const totalItems = computed(() => {
  return cart.value.reduce((total, item) => {
    return total + item.quantity
  }, 0)
})

/* =========================
   TOTAL PRICE
========================= */
const totalPrice = computed(() => {
  return cart.value
    .reduce((total, item) => {
      return total + Number(item.price) * item.quantity
    }, 0)
    .toFixed(2)
})

/* =========================
   INCREASE QUANTITY
========================= */
const increaseQty = index => {
  cart.value[index].quantity++
  saveCart()
}

/* =========================
   DECREASE QUANTITY
========================= */
const decreaseQty = index => {
  if (cart.value[index].quantity > 1) {
    cart.value[index].quantity--
    saveCart()
  }
}

/* =========================
   REMOVE ITEM
========================= */
const removeItem = index => {
  const item = cart.value[index]

  cart.value.splice(index, 1)
  saveCart()

  toast.add({
    title: 'Removed from Cart',
    description: `${item.title} removed from your cart.`,
    color: 'error'
  })
}

/* =========================
   CLEAR CART
========================= */
const clearCart = () => {
  cart.value = []
  localStorage.removeItem('cart')

  toast.add({
    title: 'Cart Cleared',
    description: 'All products have been removed.',
    color: 'success'
  })
}
</script>

<template>
  <UMain class="min-h-screen bg-[#0b1224]">
    <!-- =========================
         PAGE HEADER
    ========================== -->
    <section class="border-b border-gray-800">
      <UContainer class="py-12 text-center sm:py-14">
        <h1 class="text-5xl font-bold mb-4  flex justify-center gap-3">
          <span class="bg-blue-500 bg-clip-text text-transparent">
            Your Cart
          </span>
          <UIcon name="i-lucide-shopping-cart" class="text-5xl text-blue-500" />
        </h1>

        <p class="mt-4 text-blue-200">
          Review your items before checkout.
        </p>
      </UContainer>
    </section>

    <!-- =========================
         EMPTY CART
    ========================== -->
    <UContainer
      v-if="cart.length === 0"
      class="py-20">
      <div
        class="mx-auto max-w-xl rounded-2xl border border-gray-800 bg-[#111827] p-10 text-center shadow-xl">
        <div
          class="mx-auto flex h-20 w-20 items-center justify-center rounded-full bg-blue-500/10">
          <UIcon
            name="i-lucide-shopping-cart"
            class="h-10 w-10 text-blue-400" />
        </div>

        <h2 class="mt-6 text-2xl font-bold text-white">
          Your Cart is Empty
        </h2>

        <p class="mt-3 text-gray-400">
          Looks like you haven't added anything to your cart yet.
        </p>

        <UButton
          to="/products"
          size="lg"
          class="mt-7 bg-linear-to-r from-blue-600 to-purple-600 text-white hover:from-blue-500 hover:to-purple-500">
          Start Shopping 🛍️
        </UButton>
      </div>
    </UContainer>

    <!-- =========================
     CART CONTENT
========================== -->
    <UContainer
      v-else
      class="py-12">
      <div class="grid items-start gap-8 lg:grid-cols-3">
        <!-- LEFT: CART ITEMS -->
        <div class="lg:col-span-2">
          <div class="flex items-center justify-between mb-5">
            <div>
              <h2 class="text-2xl font-bold text-white">
                Cart Items
              </h2>

              <p class="mt-1 text-sm text-gray-400">
                {{ totalItems }}
                {{ totalItems === 1 ? 'item' : 'items' }}
                in your cart
              </p>
            </div>

            <button
              class="text-sm font-semibold text-red-400 transition hover:text-red-300"
              @click="clearCart">
              Clear Cart
            </button>
          </div>

          <!-- Product Cards -->
          <div class="space-y-5">
            <div
              v-for="(item, index) in cart"
              :key="item.productId"
              class="group rounded-2xl border border-gray-800 bg-[#111827] p-4 shadow-lg transition duration-300 hover:border-blue-500/50 hover:shadow-blue-500/5 sm:p-5">
              <div class="flex flex-col gap-5 sm:flex-row sm:items-center">
                <!-- Image -->
                <div
                  class="h-28 w-full shrink-0 overflow-hidden rounded-xl bg-[#0f172a] sm:h-28 sm:w-28">
                  <img
                    :src="item.image || '/images/placeholder.png'"
                    :alt="item.title"
                    class="h-full w-full object-cover transition duration-500 group-hover:scale-105">
                </div>

                <!-- Product Info -->
                <div class="min-w-0 flex-1">
                  <p class="text-xs font-semibold uppercase tracking-wider text-blue-400">
                    Smart Shop
                  </p>

                  <h3 class="mt-1 truncate text-lg font-bold text-white">
                    {{ item.title }}
                  </h3>

                  <p
                    class="mt-1 bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-lg font-bold text-transparent">
                    ${{ Number(item.price).toFixed(2) }}
                  </p>

                  <!-- Quantity -->
                  <div class="mt-4 flex items-center gap-3">
                    <span class="text-sm text-gray-400">
                      Quantity:
                    </span>

                    <div
                      class="flex items-center overflow-hidden rounded-lg border border-gray-700 bg-[#0b1224]">
                      <button
                        :disabled="item.quantity === 1"
                        class="flex h-8 w-8 items-center justify-center text-gray-300 hover:bg-blue-600 hover:text-white disabled:opacity-40"
                        @click="decreaseQty(index)">
                        −
                      </button>

                      <span
                        class="flex h-8 min-w-9 items-center justify-center border-x border-gray-700 px-2 text-sm font-semibold text-white">
                        {{ item.quantity }}
                      </span>

                      <button
                        class="flex h-8 w-8 items-center justify-center text-gray-300 hover:bg-purple-600 hover:text-white"
                        @click="increaseQty(index)">
                        +
                      </button>
                    </div>
                  </div>
                </div>

                <!-- Remove -->
                <button
                  class="self-start rounded-lg p-2 text-gray-500 transition hover:bg-red-500/10 hover:text-red-400 sm:self-center"
                  title="Remove item"
                  @click="removeItem(index)">
                  <UIcon
                    name="i-lucide-trash-2"
                    class="h-5 w-5" />
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- =========================
     ORDER SUMMARY
========================= -->

        <div
          class="rounded-2xl border border-gray-800 bg-[#111827] p-6 shadow-xl">
          <h2 class="mt-0 text-2xl font-bold text-white">
            Order Summary
          </h2>

          <div class="my-6 h-px bg-gray-800" />

          <!-- Items -->
          <div class="flex justify-between text-gray-400">
            <span>Items</span>

            <span class="font-medium text-white">
              {{ totalItems }}
            </span>
          </div>

          <!-- Subtotal -->
          <div class="mt-4 flex justify-between text-gray-400">
            <span>Subtotal</span>

            <span class="font-medium text-white">
              ${{ totalPrice }}
            </span>
          </div>

          <!-- Shipping -->
          <div class="mt-4 flex justify-between text-gray-400">
            <span>Shipping</span>

            <span class="font-medium text-green-400">
              Free
            </span>
          </div>

          <div class="my-6 h-px bg-gray-800" />

          <!-- Total -->
          <div class="flex items-center justify-between">
            <span class="text-lg font-semibold text-white">
              Total
            </span>

            <span
              class="bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-2xl font-extrabold text-transparent">
              ${{ totalPrice }}
            </span>
          </div>

          <!-- Checkout -->
          <UButton
            to="/checkout"
            size="lg"
            block
            class="mt-7 bg-linear-to-r from-blue-600 to-purple-600 font-semibold text-white transition hover:from-blue-500 hover:to-purple-500">
            Proceed to Checkout
          </UButton>

          <!-- Continue Shopping -->
          <UButton
            to="/products"
            variant="outline"
            block
            class="mt-3 border-gray-700 text-gray-300 hover:border-blue-500 hover:text-blue-400">
            Continue Shopping
          </UButton>
        </div>
      </div>
    </UContainer>
  </UMain>
</template>
