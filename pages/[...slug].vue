<template>
  <UContainer>
    <UPage>
      <UPageHeader :title="page.title" :description="page.description" />
      <UPageBody prose>
        <ContentRenderer v-if="page.body" :value="page" />
      </UPageBody>
    </UPage>
  </UContainer>
</template>

<script setup lang="ts">
  const route = useRoute()

  const { date: page } = await useAsncData(route.path, () => queryContent{route.path).findOne())
  if (!page.value) {
    throw createError({statusCode 404, statusMessage: 'Page not found'})
  }
</script>
