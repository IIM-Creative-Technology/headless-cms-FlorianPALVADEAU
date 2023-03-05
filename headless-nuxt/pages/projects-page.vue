<template>
    <div class="buttonContainer">
        <button @click="filterProjet('all')">reset</button>
        <div class="typeFilters">
            <button v-for="type in types" @click="filterProjet(type)">{{ type }}</button>
        </div>
        <div class="technoFilters">
            <button v-for="techno in technologies" @click="filterProjet(techno)">{{ techno }}</button>
        </div>
    </div>
  
    <div class="projectsContainer" v-if="projets" v-for="projet in filteredProjects">
        <div class="project">
            <img :src="projet.thumbnail.url" :alt="projet.short_name">
            <div>
                <h2>
                    <nuxtLink :to="`/projects/${projet.slug}`">
                        {{ projet.short_name }}
                    </nuxtLink>
                </h2>
                <p>{{ projet.short_description }}</p>
                <ul>
                    <li v-for="techno in projet.technologies">{{ techno.name }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>
  
<script setup>
    const { find } = useStrapi()
    const projets = ref()
    const types = ref([])
    const technologies = ref([])
    const activeFilter = ref("all")

    const filteredProjects = computed(() => {
        if (activeFilter.value === "all") {
            return projets.value.data
        } else {
            var test = null
            technologies.value.forEach(el => { 
                if (el === activeFilter.value) {
                    test = true
                }
            })
            if (test) {
                var filterActive = []
                projets.value.data.forEach(p => {
                    p.technologies.forEach(t => {
                        if (t.name === activeFilter.value) {
                            filterActive.push(p)
                        }
                    });
                })
                return filterActive
            } else {
                var filterActive =  projets.value.data.filter( projet => projet.type === activeFilter.value )
                return filterActive
            }
        }
    })

    const filterProjet = (filter) => {
        activeFilter.value = filter
    }

    onMounted(async () => {
        projets.value = await find('projets', {populate: 'deep'})
        types.value = new Set(projets.value.data.map(projet => { return projet.type}))
        
        var projectTechnologies = []
        projets.value.data.forEach(element => {
            element.technologies.forEach(techno => {
                var index = projectTechnologies.indexOf(techno.name)
                if (index === -1) {
                    projectTechnologies.push(techno.name)
                }
            })
        })
        technologies.value = new Set(projectTechnologies)
    })
</script>
  
<style lang="scss" scoped>
    $background-color: #EDF2FB;
    $border-color: #ABC4FF;
    $text-color: #1E202B;
    $text-color-lighter: #4A4E69;
    .buttonContainer{
        width: 100%;
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        button{
            width: 5vw;
            background-color: $border-color;
            color: white;
            border: 0;
            height: 3vh;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 5%;
            cursor: pointer;
        }

        .typeFilters{
            width: 30vw;
            height: 20%;
            display: flex;
            justify-content: space-around;
            align-items: center;
        }
        .technoFilters{
            width: 80vw;
            height: 20%;
            display: flex;
            justify-content: space-around;
            align-items: center;
        }

    }
    .projectsContainer{
        font-family: 'Poppins', sans-serif;
        margin-bottom: 20vh;
        width: 90vw;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        .project{
            width: 100%;
            height: 50vh;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10vh;
            cursor: pointer;
            img{
                width: 50%;
                height: 100%;
                object-fit: cover;
                object-position: center;
                filter: brightness(70%);
                transition:0.2s ease-in-out;
            }
            div{
                width: 50%;
                height: 100%;
                display: flex;
                justify-content: space-around;
                align-items: flex-end;
                flex-direction: column;    
                background-color: #d9dee9;
                text-align: right;
                padding-inline: 50px;
                h2{
                    font-size: 55px;
                    font-weight: 500;
                    margin-top: 10%;
                }
                p{
                    margin-top: -13%;
                    font-size: 16px;
                    font-weight: 300;
                    font-style: italic;
                }
                ul{
                    list-style-type: none;
                    width: 100%;
                    display: flex;
                    justify-content: flex-end;
                    flex-wrap: wrap;
                    li{
                        margin-right: 0;
                        margin-left: 15%;
                        font-size: 14px;
                        font-style: italic;
                        font-weight: 200;
                        margin-bottom: 5%;
                        text-decoration: none;
                    }
                    :nth-child(1){
                        margin: 0;
                    }

                }
            }
        }
        :nth-child(even){
            flex-direction: row-reverse;
            div{
                text-align: left;
                align-items: flex-start;
                ul{
                    justify-content: flex-start;
                    li{
                        margin-left: 0;
                        margin-right: 15%;
                    }
                    :nth-last-child(1){
                        margin: 0;
                    }
                    :nth-child(1){
                        margin-left: 0;
                        margin-right: 15%;
                    }
                }
            }
        }
    }
    @media screen and (max-width: 1370px) {
        body{
            .projectsContainer{
                margin-bottom: 20vh;
                width: 90vw;
                flex-direction: column;
                .project{
                    width: 100%;
                    height: 50vh;
                    display: flex;
                    justify-content: space-between;
                    margin-top: 10vh;
                    img{
                        width: 50%;
                        height: 100%;
                    }
                    div{
                        width: 50%;
                        height: 100%;
                        padding-inline: 50px;
                        h2{
                            font-size: 45px;
                            font-weight: 500;
                            margin-top: 10%;
                        }
                        p{
                            margin-top: -13%;
                            font-size: 16px;
                            font-weight: 300;
                        }
                        ul{
                            width: 100%;
                            li{
                                margin-right: 0;
                                margin-left: 15%;
                                font-size: 12px;
                            }
                            :nth-child(1){
                                margin: 0;
                            }
        
                        }
                    }
                }
                :nth-child(even){
                    flex-direction: row-reverse;
                    div{
                        text-align: left;
                        align-items: flex-start;
                        ul{
                            justify-content: flex-start;
                            li{
                                margin-left: 0;
                                margin-right: 15%;
                            }
                            :nth-last-child(1){
                                margin: 0;
                            }
                            :nth-child(1){
                                margin-left: 0;
                                margin-right: 15%;
                            }
                        }
                    }
                }
            }
        }
    }
    @media screen and (max-width: 1000px) {
        body{
            .projectsContainer{
                width: 95vw;
            }
        }
    }
    @media screen and (max-width: 800px) {
        body{
            width: 100vw;
            .projectsContainer{
                margin-bottom: 20vh;
                width: 90vw;
                flex-direction: column;
                .project{
                    width: 100%;
                    height: 60vh;
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: space-between;
                    margin-top: 5vh;
                    img{
                        width: 100%;
                        height: 60%;
                    }
                    div{
                        width: 100%;
                        height: 40%;
                        padding: 0;
                        align-items: center;
                        text-align: center;

                        h2{
                            font-size: 35px;
                            margin-top: 0%;
                        }
                        p{
                            padding: 10px;
                            font-size: 14px;
                            margin-top: -2%;
                        }
                        ul{
                            justify-content: center;
                        }
                    }
                }
                :nth-child(even){
                    flex-direction: column;
                    div{
                        text-align: center;
                        align-items: center;
                        ul{
                            justify-content: center;
                        }
                    }
                }
            }
        }
    }
</style>