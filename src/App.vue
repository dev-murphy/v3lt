<script lang="ts" setup>
import { useAppStore } from "@/stores/app";

const appStore = useAppStore();
</script>

<template>
  <div
    class="min-h-screen bg-black flex items-center justify-center text-3xl md:text-5xl text-white font-bold"
  >
    <p>Welcome to {{ appStore.name }}</p>
  </div>
</template>
