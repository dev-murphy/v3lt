<script lang="ts" setup>
const appStore = useAppStore();

const isCopied = ref(false);
const projectName = ref("");

function copyCommand(text: string) {
  navigator.clipboard
    .writeText(text)
    .then(() => {
      isCopied.value = true;
      setTimeout(() => {
        isCopied.value = false;
      }, 1000);
      console.log("Text copied to clipboard");
    })
    .catch((err) => {
      console.error("Failed to copy text: ", err);
    });
}

function removeSpaces() {
  projectName.value = projectName.value.replace(/\s/g, "");
}
</script>

<template>
  <div
    class="min-h-screen bg-linear-to-br from-black to-neutral-800 flex flex-col items-center justify-center px-4"
  >
    <h1 class="text-3xl md:text-5xl text-neutral-400 font-bold">
      Welcome to {{ appStore.name }}
    </h1>
    <p class="mt-1 text-white text-center text-xl">
      This is another opinionated Vue 3 project with Typescript
    </p>
    <ul
      class="flex flex-wrap items-center justify-center list-none mt-3 text-sm"
    >
      <li>
        <a href="#">UI Library</a>
      </li>
      <li>
        <a href="#">State management</a>
      </li>
      <li>
        <a href="#">File-based Routing</a>
      </li>
      <li>
        <a href="#">Vue Directives</a>
      </li>
      <li>
        <a href="#">Components</a>
      </li>
    </ul>

    <div class="relative mt-8">
      <div
        class="flex items-center justify-center gap-x-2 md:gap-x-6 bg-neutral-800 border border-neutral-700 hover:border-neutral-600 p-2.5 pb-3 font-mono text-neutral-300 rounded-lg"
      >
        <div class="flex text-sm">
          <p>npx degit dev-murphy/v3lt</p>
          <input
            type="text"
            v-model="projectName"
            @keydown.space.prevent
            @input="removeSpaces"
            placeholder="my-project"
            class="pl-2 outline-none"
          />
        </div>

        <button
          @click="
            copyCommand(
              `npx degit dev-murphy/v3lt ${projectName || 'my-project'}`
            )
          "
        >
          <Copy
            class="w-5 h-5 text-neutral-600 hover:text-white cursor-pointer"
          />
        </button>
      </div>

      <p
        class="absolute top-full left-1/2 translate-y-1 -translate-x-1/2 font-mono text-lg text-center text-white transition-all"
        :class="{
          'opacity-100 translate-y-0 ': isCopied,
          'opacity-0 translate-y-5': !isCopied,
        }"
      >
        Copied!
      </p>
    </div>
  </div>
</template>

<style scoped>
@import "tailwindcss";

ul li {
  @apply relative pl-6 font-bold text-neutral-600 hover:text-white transition-colors duration-150 uppercase;
}

ul li:not(:last-child)::before {
  @apply absolute content-[''] top-1/2 -right-4 -translate-y-1/2 w-1.5 h-1.5 bg-emerald-500 rounded-full;
}
</style>
