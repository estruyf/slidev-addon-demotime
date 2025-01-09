<script setup lang="ts">
import { useSlideContext } from '@slidev/client';
import { ref } from 'vue';

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
  image: {
    type: String,
    default: '/demo-time.svg',
  },
});

const context = useSlideContext();
const { $page, $clicks, $renderContext, $nav } = context;

const runDemo = ref(false)
</script>

<template>
  <trigger-action
    :id="props.id"
    :port="props.port"
    :host="props.host"
    v-if="($page === $nav.currentPage && $clicks === parseInt(props.click) && $renderContext !== 'overview') || runDemo">
    {{ $renderContext }}
  </trigger-action>
  
  <button class="absolute bottom-2 right-2 group flex items-center" @click="runDemo = true">
    <div class="hidden text-[8px] group-hover:flex flex-col justify-center text-left bg-black text-white p-1 h-[33px] -mr-4 pr-5 rounded-l">
      <p class="!m-0 !mb-[2px] !p-0 !leading-tight">
        <span class="w-[45px] inline-block">Demo ID:</span>
        <code class="!m-0 !p-0" style="background:transparent !important;color:white !important;">{{ props.id }}</code>
      </p>
    </div>
    
    <img
      :src="props.image" 
      width="36px" />
  </button>
</template>
