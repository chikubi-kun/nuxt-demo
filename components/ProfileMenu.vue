<template>
  <Menu as="div" class="relative ml-3 text-gray-900 dark:text-gray-400">
    <div>
      <MenuButton class="flex rounded-full p-1 hover:bg-gray-700 hover:text-white focus:outline-none">
        <span class="sr-only">Open user menu</span>
        <UserIcon class="h-6 w-6" aria-hidden="true" />
      </MenuButton>
    </div>
    <Transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transform opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transform opacity-100 scale-100"
      leave-to-class="transform opacity-0 scale-95"
    >
      <MenuItems class="absolute right-0 z-10 mt-2 w-auto whitespace-nowrap origin-top-right rounded-md bg-white dark:bg-gray-700 py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">
        <MenuItem
          v-slot="{ active }"
          v-for="item in profile"
          :key="item.name"
        >
          <NuxtLink
            :to="item.to"
            :class="[active ? 'bg-gray-100 dark:bg-gray-600' : '', $route.path === item.to ? 'bg-primary text-white' : '', 'block px-4 py-2 text-sm']"
          >
            {{ item.name }}
          </NuxtLink>
        </MenuItem>
      </MenuItems>
    </Transition>
  </Menu>
</template>

<script setup lang="ts">
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { UserIcon } from '@heroicons/vue/24/outline'
const profile = [
  { name: 'Your Profile', to: '/profile' },
  { name: 'Settings', to: '/settings' },
  { name: 'Sign Out', to: '/#' }
]
</script>
