<template>
  <Listbox v-model="$colorMode.preference" as="div" class="relative text-gray-900 dark:text-gray-400">
    <div>
      <ListboxButton class="flex rounded-full p-1 hover:bg-gray-700 hover:text-white focus:outline-none">
        <span class="sr-only">Color mode</span>
        <component v-bind:is="$colorMode.value === 'dark' ? MoonIcon : SunIcon" class="h-6 w-6" aria-hidden="true" />
      </ListboxButton>
    </div>
    <Transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transform opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transform opacity-100 scale-100"
      leave-to-class="transform opacity-0 scale-95"
      class-name="absolute mb-1 w-full rounded-md bg-white shadow-lg bottom-full"
    >
      <ListboxOptions class="absolute right-0 z-10 mt-2 w-auto origin-top-right rounded-md bg-white dark:bg-gray-700 py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">
        <ListboxOption
          v-slot="{ active, selected }"
          v-for="item in modes"
          :key="item.key"
          :value="item.val"
          as="template"
        >
          <li :class="[active ? 'bg-gray-100 dark:bg-gray-600' : '', selected ? 'bg-primary text-white' : '', 'flex px-4 py-2 text-sm items-center']">
            <component v-bind:is="item.icon" class="h-6 w-6" aria-hidden="true" />
            <span class="pl-2" >{{ item.key }}</span>
          </li>
        </ListboxOption>
      </ListboxOptions>
    </Transition>
  </Listbox>
</template>

<script setup lang="ts">
import { Listbox, ListboxButton, ListboxOptions, ListboxOption } from '@headlessui/vue'
import { MoonIcon, SunIcon, ComputerDesktopIcon } from '@heroicons/vue/24/outline'

const modes = [
  { key: 'Dark', val:'dark', icon: MoonIcon },
  { key: 'Light', val:'light', icon: SunIcon },
  { key: 'System', val:'system', icon: ComputerDesktopIcon },
]
</script>
