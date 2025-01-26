<script lang="ts">
useHead({
  title: 'Bubblewrap Discord',
  link: [
    { rel: 'icon', type: 'image/png', href: '/favicon.png' },
  ],
  meta: [{ name: 'apple-mobile-web-app-title', content: 'Bubblewrap Discord' }],
  htmlAttrs: {
    class: 'dark',
  },
})
</script>

<template>
  <NuxtRouteAnnouncer />
  <NuxtLoadingIndicator />
  <NuxtPage />
  <UNotifications />
</template>
