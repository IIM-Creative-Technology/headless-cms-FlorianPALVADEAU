<template v-if="projet">
    <button href="/">← go back</button>
    <iframe
        v-if="projet.video_link"
        :src=projet.video_link 
        :title=projet.short_name 
        frameBorder="0" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowFullScreen>
    </iframe>
    <div className='projectContent'>
        <h2>{{projet.full_name}}.</h2>
        <p className='desc'>{{projet.full_description}} 
            <a v-if="projet.other_link" :href=projet.other_link target='_blank' rel='noreferrer'>see my dropbox.</a> <a v-if="projet.link_cars" :href=projet.link_cars target='_blank' rel='noreferrer'>See my post about this project.</a></p>
        <div className='projectInfo'>
            <p v-if="projet.difficulty">Difficulty : {{projet.difficulty}}</p>
            <p v-if="projet.client">Client : {{projet.client}}</p>
        </div>
    </div>
</template>

<script setup>
    const { findOne } = useStrapi()
    const route = useRoute()
    const projet = ref()

    onMounted( async() => {
        projet.value = await findOne(`projets?filters[slug]=${route.params.slug}&populate=deep`)
        projet.value = projet.value.data[0]
        console.log(projet);
    })
</script>