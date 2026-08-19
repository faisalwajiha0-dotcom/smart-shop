<script setup>
const route = useRoute()
const toast = useToast()

const products = [
  {
    id: 1,
    title: 'Wireless Headphones',
    category: 'Electronics',
    price: 49.99,
    rating: 4.8,
    image:
      'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=1000&q=80',
    description:
      'Enjoy high-quality sound with these comfortable wireless headphones. Perfect for music, study and everyday use.',
    features: [
      'Wireless connectivity',
      'High-quality sound',
      'Comfortable design',
      'Long battery life'
    ]
  },
  {
    id: 2,
    title: 'Smart Watch',
    category: 'Accessories',
    price: 79.99,
    rating: 4.7,
    image:
      'https://images.unsplash.com/photo-1523275335684-37898b6baf30?auto=format&fit=crop&w=1000&q=80',
    description:
      'A modern smart watch designed to keep you connected and organized throughout your day.',
    features: [
      'Modern design',
      'Fitness tracking',
      'Smart notifications',
      'Comfortable strap'
    ]
  },
  {
    id: 3,
    title: 'Classic Sneakers',
    category: 'Footwear',
    price: 59.99,
    rating: 4.6,
    image:
      'https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=1000&q=80',
    description:
      'Comfortable and stylish sneakers suitable for everyday wear and casual outings.',
    features: [
      'Comfortable fit',
      'Modern style',
      'Durable sole',
      'Everyday wear'
    ]
  },
  {
    id: 4,
    title: 'Casual T-Shirt',
    category: 'Fashion',
    price: 29.99,
    rating: 4.5,
    image:
      'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?auto=format&fit=crop&w=1000&q=80',
    description:
      'A simple and comfortable casual T-shirt that is perfect for everyday style.',
    features: [
      'Soft fabric',
      'Comfortable fit',
      'Casual design',
      'Easy to wear'
    ]
  },
  {
    id: 5,
    title: 'Laptop',
    category: 'Electronics',
    price: 799.99,
    rating: 4.9,
    image:
      'https://images.unsplash.com/photo-1496181133206-80ce9b88a853?auto=format&fit=crop&w=1000&q=80',
    description:
      'A powerful and stylish laptop suitable for work, study and everyday tasks.',
    features: [
      'Powerful performance',
      'Modern design',
      'High-quality display',
      'Portable'
    ]
  },
  {
    id: 6,
    title: 'Backpack',
    category: 'Accessories',
    price: 39.99,
    rating: 4.4,
    image:
      'https://images.unsplash.com/photo-1553062407-98eeb64c6a62?auto=format&fit=crop&w=1000&q=80',
    description:
      'A practical backpack with enough space for your everyday essentials.',
    features: [
      'Spacious design',
      'Comfortable straps',
      'Durable material',
      'Everyday use'
    ]
  }
]

const product = computed(() => {
  return products.find(
    item => item.id === Number(route.params.id)
  )
})

/* 🛒 Add Product to Cart */
const addToCart = () => {
  if (!product.value) return

  const savedCart = localStorage.getItem('cart')
  const cart = savedCart ? JSON.parse(savedCart) : []

  const existingProduct = cart.find(
    item => item.productId === product.value.id
  )

  if (existingProduct) {
    existingProduct.quantity += 1
  }
  else {
    cart.push({
      productId: product.value.id,
      title: product.value.title,
      price: product.value.price,
      image: product.value.image,
      quantity: 1
    })
  }

  localStorage.setItem('cart', JSON.stringify(cart))

  toast.add({
    title: 'Added to Cart 🛒',
    description: `${product.value.title} has been added to your cart.`,
    color: 'success'
  })
}
</script>

<template>
  <UMain class="min-h-screen bg-[#0b1224]">
    <UContainer class="py-12 sm:py-16">
      <!-- Back Button -->
      <UButton
        to="/products"
        variant="ghost"
        class="mb-8 text-gray-400 hover:text-white">
        ← Back to Products
      </UButton>

      <!-- Product Found -->
      <div
        v-if="product"
        class="grid gap-10 lg:grid-cols-2">
        <!-- Product Image -->
        <div
          class="overflow-hidden rounded-3xl border border-gray-800 bg-[#111827]">
          <img
            :src="product.image"
            :alt="product.title"
            class="h-112.5 w-full object-cover">
        </div>

        <!-- Product Information -->
        <div class="flex flex-col justify-center">
          <!-- Category -->
          <p
            class="text-sm font-semibold uppercase tracking-widest text-blue-400">
            {{ product.category }}
          </p>

          <!-- Title -->
          <h1
            class="mt-3 bg-linear-to-r from-blue-400 to-purple-500 bg-clip-text text-4xl font-extrabold text-transparent sm:text-5xl">
            {{ product.title }}
          </h1>

          <!-- Rating -->
          <div class="mt-5 text-yellow-400">
            ⭐ {{ product.rating }} / 5
          </div>

          <!-- Price -->
          <p
            class="mt-6 text-3xl font-bold text-white">
            ${{ product.price }}
          </p>

          <!-- Description -->
          <p
            class="mt-6 text-lg leading-8 text-gray-400">
            {{ product.description }}
          </p>

          <!-- Features -->
          <div class="mt-8">
            <h2 class="text-xl font-bold text-white">
              Product Features
            </h2>

            <ul class="mt-4 space-y-3">
              <li
                v-for="feature in product.features"
                :key="feature"
                class="flex items-center gap-3 text-gray-300">
                <span class="text-blue-400">✓</span>
                {{ feature }}
              </li>
            </ul>
          </div>

          <!-- Button -->
          <div class="mt-10 flex gap-4">
            <UButton
              size="lg"
              class="bg-linear-to-r from-blue-600 to-purple-600 text-white transition hover:from-blue-500 hover:to-purple-500"
              @click="addToCart">
              🛒 Add to Cart
            </UButton>

            <UButton
              to="/products"
              size="lg"
              variant="outline">
              Continue Shopping
            </UButton>
          </div>
        </div>
      </div>

      <!-- Product Not Found -->
      <div
        v-else
        class="py-20 text-center">
        <div class="text-6xl">
          🔍
        </div>

        <h1 class="mt-5 text-3xl font-bold text-white">
          Product Not Found
        </h1>

        <p class="mt-3 text-gray-400">
          Sorry, this product does not exist.
        </p>

        <UButton
          to="/products"
          class="mt-6">
          Back to Products
        </UButton>
      </div>
    </UContainer>
  </UMain>
</template>
