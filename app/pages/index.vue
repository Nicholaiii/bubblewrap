<script setup lang="ts">
const source = ref('')
const { copy, copied, isSupported } = useClipboard({ source })
const bubblewrap = (text: string): string => text === '' ? '' : '||' + text.split('').join('||') + '||'
</script>

<template>
  <div class="grid grid-cols-6 py-2 justify-items-stretch text-zinc-200 ">
    <h1 class="col-span-6 md:col-span-2 md:col-start-3 text-4xl py-4">
      <span v-for="letter, key in 'BUBBLEWRAP'.split('')" :key class="bg-zinc-800 rounded-xl px-2">{{ letter }}</span>
    </h1>
    <span class="col-span-6 md:col-span-2 py-2" />
    <div class="col-span-6 md:col-span-2  md:col-start-3">
      <UInput
        v-model="source"
        color="rose"
        class="justify-self-center"
        placeholder="Type your message here"
      />
    </div>
    <span class="col-span-6 md:col-span-2" />
    <template v-if="source !== ''">
      <h2 class="col-span-6 md:col-span-4 md:col-start-3 text-xl py-2">
        Result:
      </h2>
      <span class="col-span-6 md:col-span-2" />

      <div class="col-span-6 md:col-span-2 md:col-start-3">
        <code class="text-sm sm:text-base inline-flex text-left items-center space-x-4 bg-zinc-800 rounded-lg p-4 pl-6">
          <span class="flex gap-4">
            <span class="flex-1">
              <span>
                {{ bubblewrap(source) }}
              </span>
            </span>
          </span>
          <UButton
            v-if="isSupported"
            icon="i-lucide-clipboard-copy"
            size="sm"
            color="rose"
            variant="outline"
            class="shrink-0"
            @click="copy(bubblewrap(source))"
          >{{ copied ? 'Copied!' : '&nbsp;Copy&nbsp;' }}</UButton>
        </code>
      </div>
      <span class="col-span-6 md:col-span-2 py-2" />
      <span v-if="!isSupported" class="col-span-6">Clipboard API is not supported. Copy it yourself</span>
    </template>
    <span class="col-span-6 md:col-span-2 md:col-start-3 py-2 text-zinc-600 text-lg">
      xoxo <UIcon name="i-lucide-heart" class="w-5 h-5" />  <NuxtLink to="https://nicholai.dev" external class="font-bold underline">nicholai.dev</NuxtLink>
    </span>
  </div>
</template>
