<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'Home',
    to: '/',
  },
  {
    label: 'Products',
    to: '/products',
  },
  {
    label: 'Cart',
    to: '/cart',
  },
  {
    label: 'Checkout',
    to: '/checkout',
  },
  {
    label: 'About',
    to: '/about',
  },
  {
    label: 'Contact',
    to: '/contact',
  }
])
</script>

<template>
  <UHeader class="bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent">
    <template #title>
      <span class="text-4xl font-bold bg-linear-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent">Smart Shop</span>
    </template>
    <template #right>
      <UNavigationMenu :items="items" class="[&_a]:text-blue-400 [&_a:hover]:text-purple-500" />
    </template>
  </UHeader>
</template>
