<script setup>
import { Link } from '@inertiajs/vue3';

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <nav class="text-sm text-gray-600 mb-4 flex items-center space-x-1">
    <template v-for="(item, index) in items" :key="index">
      <div class="flex items-center">
        <Link
          v-if="item.href"
          :href="item.href"
          class="hover:underline text-green-700 font-medium"
        >
          {{ item.label }}
        </Link>
        <span v-else class="text-gray-500">{{ item.label }}</span>
        <span v-if="index < items.length - 1" class="mx-2 text-gray-400">›</span>
      </div>
    </template>
  </nav>
</template>
