<template>
    <div v-if="projets">
        <h1>Contact</h1>
        <nuxt-link :to="`/projets/${projet.slug}`" v-for="projet in projets.data">
            {{ projet.short_name }}
        </nuxt-link>
    </div>
  </template>
  
  <script setup>
  const { find } = useStrapi()
  const projets = ref()
  
  onMounted(async () => {
    projets.value = await find('projets', {populate: 'deep'})
  })
  
  </script>
  
  <style lang="scss" scoped></style>