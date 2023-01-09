<template>
  <NuxtLoadingIndicator />
  <Disclosure as="nav" class="bg-neutral-50 dark:bg-gray-800" v-slot="{ open }">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="relative flex h-16 items-center justify-between">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <!-- Mobile menu button-->
          <DisclosureButton class="inline-flex items-center justify-center rounded-md p-2 text-gray-900 dark:text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-primary">
            <span class="sr-only">Open main menu</span>
            <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
            <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
          </DisclosureButton>
        </div>
        <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
          <div class="flex flex-shrink-0 items-center">
            <img class="block h-6 w-auto lg:hidden" src="~/assets/logo.svg" alt="Your Company" />
            <img class="hidden h-6 w-auto lg:block" src="~/assets/logo.svg" alt="Your Company" />
          </div>
          <div class="hidden sm:ml-6 sm:block">
            <div class="flex space-x-4">
              <NuxtLink
                v-for="item in navigation"
                :key="item.name"
                :to="item.to"
                :class="[item.to === $route.path ? 'bg-primary text-white' : 'text-gray-900 dark:text-gray-400 hover:bg-gray-700 hover:text-white', 'px-3 py-2 rounded-md text-sm font-medium']"
                :aria-current="item.to === $route.path ? 'page' : undefined"
              >
                {{ item.name }}
              </NuxtLink>
            </div>
          </div>
        </div>
        <div class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
          <ThemeSelect />
          <Notifications />
          <ProfileMenu />
        </div>
      </div>
    </div>

    <DisclosurePanel class="sm:hidden">
      <div class="space-y-1 px-2 pt-2 pb-3">
        <DisclosureButton
          v-for="item in navigation"
          :key="item.name"
          :class="[item.to === $route.path ? 'bg-primary text-white' : 'text-gray-900 dark:text-gray-400 hover:bg-gray-700 hover:text-white', 'px-3 py-2 rounded-md text-base']"
          :aria-current="item.to === $route.path ? 'page' : undefined"
          as="div"
        >
          <NuxtLink :to="item.to" class="block font-medium">{{ item.name }}</NuxtLink>
        </DisclosureButton>
      </div>
    </DisclosurePanel>
  </Disclosure>
</template>

<script setup lang="ts">
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'   //'@heroicons/vue/24/outline'

const navigation = [
  { name: 'Home', to: '/' },
  { name: 'Series', to: '/series' },
  { name: 'Schedule', to: '/schedule' },
]
</script>
