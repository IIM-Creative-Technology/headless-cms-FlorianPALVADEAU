<template>
    <div v-if="projets">
        <h1>Projets</h1>
        <nuxt-link :to="`/projets/${projet.slug}`" v-for="projet in filteredProjects">
            {{ projet.short_name }}
        </nuxt-link>
    </div>
</template>

<script setup>
    const { find } = useStrapi()
    const projets = ref()
    const types = ref([])
    const activeFilter = ref("all")

    const filteredProjects = computed(() => {
        if (activeFilter === "all") {
            return projets.value.data
        }
        return projets.value.data.filter(projet => projet.type === activeFilter.value)
    })

    const filterProjet = (type) => {
        activeFilter.value = type
    }

    onMounted(async () => {
        projets.value = await find('projets', {populate: 'deep'})
        types.value = new Set(projets.value.data.map(projet => { return projet.type}))
    })
</script>

<style lang="scss" scoped></style>