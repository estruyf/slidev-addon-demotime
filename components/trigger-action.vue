<script setup lang="ts">
import { onMounted, onUnmounted, } from 'vue'

declare global {
  interface Window {
    demos: string[];
  }
}

const props = defineProps({
  click: {
    type: String,
    default: 1,
  },
  id: {
    type: String,
    required: true,
  },
  port: {
    type: Number,
    default: 3710,
  },
  host: {
    type: String,
    default: 'http://localhost',
  },
});

onMounted(() => {
  const apiUrl = `${props.host}:${props.port}/api/runById`;
  const id = props.id;

  if (!id) {
    return;
  }

  const body = {
    id
  };

  window.demos = window.demos || [];
  if (!window.demos.includes(id)) {
    window.demos = [...window.demos, id];

    fetch(apiUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(body),
    });
  }
});
</script>

<template>
  <div class="hidden">{{ props.id }}</div>
</template>
