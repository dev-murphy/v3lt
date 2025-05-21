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
    class="w-creen min-h-dvh bg-linear-to-br from-black to-neutral-800 flex flex-col items-center justify-center font-[Inter_Tight] px-4"
  >
    <h1 class="text-center text-3xl md:text-5xl text-neutral-400 font-bold">
      Welcome to {{ appStore.name }}
    </h1>

    <p class="mt-1 text-white text-center text-xl">
      This is another opinionated Vue 3 project with Typescript
    </p>

    <ul
      class="w-full flex flex-wrap items-center justify-center gap-x-2 gap-y-0.5 list-none mt-6 text-sm tracking-wider duration-150 uppercase"
    >
      <li class="text-neutral-600 hover:text-white transition-colors">
        UI Library
      </li>
      <li class="w-1.5 h-1.5 bg-emerald-500 rounded"></li>
      <li class="text-neutral-600 hover:text-white transition-colors">
        State management
      </li>
      <li class="w-1.5 h-1.5 bg-emerald-500 rounded-full"></li>
      <li class="text-neutral-600 hover:text-white transition-colors">
        File-based Routing
      </li>
      <li class="w-1.5 h-1.5 bg-emerald-500 rounded-full"></li>
      <li class="text-neutral-600 hover:text-white transition-colors">
        Vue Directives
      </li>
      <li class="w-1.5 h-1.5 bg-emerald-500 rounded-full"></li>
      <li class="text-neutral-600 hover:text-white transition-colors">
        Components
      </li>
    </ul>

    <div
      class="w-full md:w-4/5 flex items-start gap-2 bg-yellow-900/50 mt-3 p-2 border border-yellow-600 text-yellow-400 tracking-wide rounded-lg"
    >
      <Alert class="w-5 h-5 flex-shrink-0 mt-1" />
      <p>
        You can input the name of the project below.
        <b class="underline">Please Note:</b>
        For more information, please check out the source code on Github.
      </p>
    </div>

    <div class="w-full relative flex flex-col mt-8">
      <div
        class="flex items-center justify-between gap-x-0 md:gap-x-6 bg-neutral-800 border border-neutral-700 hover:border-neutral-600 p-2.5 pb-3 font-mono text-neutral-300 rounded-lg"
      >
        <div class="flex text-sm">
          <p class="hidden sm:block flex-shrink-0">npx degit dev-murphy/v3lt</p>
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

      <a
        href="https://github.com/dev-murphy/v3lt"
        class="flex items-center gap-x-2 mt-2 text-base text-neutral-300 text-center font-mono hover:underline mx-auto"
      >
        <Github class="w-5 h-5" />
        View Source Code
      </a>

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
