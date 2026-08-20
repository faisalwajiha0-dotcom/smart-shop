<script setup>
/* eslint-disable */
import { ref } from 'vue'
import { useToast } from '#imports'

const toast = useToast()

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const isSubmitting = ref(false)

const handleSubmit = async () => {
  // Check all required fields
  if (
    !formData.value.name.trim() ||
    !formData.value.email.trim() ||
    !formData.value.message.trim()
  ) {
    toast.add({
      title: 'Required Fields',
      description: 'Please enter your name, email, and message.',
      color: 'error'
    })
    return
  }

  // Simple email validation
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/

  if (!emailPattern.test(formData.value.email)) {
    toast.add({
      title: 'Invalid Email',
      description: 'Please enter a valid email address.',
      color: 'error'
    })
    return
  }

  // Sending state
  isSubmitting.value = true

  // Small delay for better UX
  await new Promise(resolve => setTimeout(resolve, 800))

  // Success
  toast.add({
    title: 'Message Successfully Sent!',
    description: 'Thank you! Your message has been sent successfully.',
    color: 'success'
  })

  // Clear form
  formData.value = {
    name: '',
    email: '',
    message: ''
  }

  isSubmitting.value = false
}
</script>

<template>
  <section class="px-6 py-16">
    <div class="mx-auto max-w-2xl">
      <div
        class="rounded-3xl border border-gray-200 bg-white p-10 shadow-xl dark:border-gray-700 dark:bg-gray-900"
      >
        <!-- Heading -->
        <div class="mb-12 text-center">
          <h1
            class="mb-3 bg-blue-500 bg-clip-text text-5xl font-extrabold text-transparent"
          >
            Contact Us
          </h1>

          <p class="text-gray-500 dark:text-blue-200">
            Have questions? We'd love to hear from you!
          </p>
        </div>

        <!-- Form -->
        <form
          class="space-y-6"
          @submit.prevent="handleSubmit"
        >
          <!-- Name -->
          <div>
            <input
              v-model="formData.name"
              type="text"
              placeholder="Enter your name"
              class="w-full rounded-xl border border-gray-300 p-3 text-gray-800 outline-none focus:ring-2 focus:ring-blue-500 dark:border-gray-700 dark:bg-gray-800 dark:text-white"
            >
          </div>

          <!-- Email -->
          <div>
            <input
              v-model="formData.email"
              type="email"
              placeholder="Enter your email"
              class="w-full rounded-xl border border-gray-300 p-3 text-gray-800 outline-none focus:ring-2 focus:ring-blue-500 dark:border-gray-700 dark:bg-gray-800 dark:text-white"
            >
          </div>

          <!-- Message -->
          <div>
            <textarea
              v-model="formData.message"
              rows="4"
              placeholder="Write your message..."
              class="w-full resize-none rounded-xl border border-gray-300 p-3 text-gray-800 outline-none focus:ring-2 focus:ring-blue-500 dark:border-gray-700 dark:bg-gray-800 dark:text-white"
            />
          </div>

          <!-- Button -->
          <button
            type="submit"
            :disabled="isSubmitting"
            class="w-full rounded-xl bg-linear-to-r from-blue-600 to-purple-600 py-3 font-semibold text-white transition hover:opacity-90 disabled:cursor-not-allowed disabled:opacity-60"
          >
            {{ isSubmitting ? 'Sending...' : 'Send Message' }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>
