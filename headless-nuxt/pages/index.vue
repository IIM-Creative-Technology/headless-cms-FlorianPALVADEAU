<template>
  <div v-if="projects">
      <h1>Hello World</h1>
      <nuxt-link :to="`/projects/${project.slug}`" v-for="project in projects.data">
          {{ project.short_name }}
      </nuxt-link>
  </div>
</template>

<script setup>
const { find } = useStrapi()
const projects = ref()

onMounted(async () => {
  projects.value = await find('projects', {populate: 'deep'})
  console.log(projects);
})

</script>

<style lang="scss" scoped></style>