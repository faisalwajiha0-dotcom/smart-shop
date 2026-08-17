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
  <UHeader>
    <template #title>
      <span class="text-3xl font-bold">Smart Shop</span>
    </template>
    <template #right>
      <UNavigationMenu :items="items" />
    </template>
  </UHeader>
</template>
