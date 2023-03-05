<template v-if="projet">
    <div class="singleProject" v-if="projet">
        <nuxtLink :to="`/projects-page`" class="button">← go back</nuxtLink>
        <iframe 
            :src="projet.video_link" 
            :title="projet.short_name" 
            frameborder="0" 
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
            allowfullscreen=""
        >
        </iframe>
        <div class="projectContent">
            <h2>{{ projet.full_name }}</h2>
            <p class="desc">{{ projet.full_description }} <a v-if="projet.dropbox_link" :href="projet.dropbox_link">see my dropbox</a> <a v-if="projet.car_link" :href="projet.car_link">See my post about this project</a></p>
            <div class="projectInfo">
                <p v-if="projet.difficulty">Difficulty : {{ projet.difficulty }}</p>
                <p v-if="projet.client">Client : {{ projet.client }}</p>
                </div>
            </div>
        <div class="moreProjects">
            <h3>More projects.</h3>
            <div class="content" >
                <nuxtLink :to="`/projects/${prevProjets[0].slug}`" v-if="prevProjets[0]" class="projet first">
                    <img :src="prevProjets[0].thumbnail.url" :alt="prevProjets[0].short_name">
                    <h4>← {{ prevProjets[0].short_name }}</h4>
                </nuxtLink>
                <nuxtLink :to="`/projects/${nextProjets[0].slug}`" v-if="nextProjets[0]" class="projet second">
                    <img :src="nextProjets[0].thumbnail.url" :alt="nextProjets[0].short_name">
                    <h4>{{ nextProjets[0].short_name }} →</h4>
                </nuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>
    const { findOne } = useStrapi()
    const { find } = useStrapi()
    const route = useRoute()
    const projet = ref()
    const projets = ref();
    const nextProjets = ref();
    const prevProjets = ref();

    onMounted( async() => {
        projets.value = await find('projets', {populate: 'deep'});
        projets.value = projets.value.data;

        projet.value = await findOne(`projets?filters[slug]=${route.params.slug}&populate=deep`)
        projet.value = projet.value.data[0]
        

        prevProjets.value = projets.value.filter((p) => p.id === projet.value.id -1);
        nextProjets.value = projets.value.filter((p) => p.id === projet.value.id +1);
        console.log(prevProjets.value);
        console.log(nextProjets.value);

        if (nextProjets.value === undefined) {
            nextProjets.value = projets.value[0];
        } 
        if (prevProjets.value === undefined) {
            prevProjets.value = projets.value[projets.value.length - 1];
        }

        // if (projet.value.id > 1 && project.value.id !== 1) {            
        //     previousProject.value = await findOne('projets', projet.value.id-1, {populate: 'deep'})
        //     previousProject.value = previousProject.value.data[0]
        //     console.log(previousProject.value)
        // }
        // if (projet.value.id < 5 && project.value.id !== 5) {
        //     nextProject.value = await findOne('projets', projet.value.id+1, {populate: 'deep'})
        //     nextProject.value = nextProject.value.data[0]
        //     console.log(nextProject.value)
        // }
    })
</script>

<style scoped lang="scss">
    .singleProject{
        width: 80vw;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        font-family: 'Poppins', sans-serif;
        margin-bottom: 30vh;
        .button{
            position: relative;
            top: 4vh;
            left: -45.5%;
            width: 10vw;
            height: 4vh;
            text-transform: uppercase;
            color: white;
            background-color: #1E202B;
            border: 0;
            font-size: 14px;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            color: red
            a{
                text-decoration: none;
            }
        }
        iframe{
            width: 70%;
            height: 55vh;
        }
        .projectContent{
            margin-top: 5vh;
            width: 70%;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            flex-direction: column;
            h2{
                font-size: 35px;
                font-weight: 500;
                margin-bottom: 3vh;
            }
            .desc{
                font-size: 16px;
                line-height: 20px;
                margin-bottom: 3vh;
            }
            .projectInfo{
                width: 50%;
                display: flex;
                justify-content: space-between;
                font-size: 14px;
                font-style: italic;
                font-weight: 300;
            }
        }
        .moreProjects{
            width: 70%;
            display: flex;
            justify-content: space-around;
            height: 20vh;
            margin-top: 15vh;
            flex-direction: column;
            align-items: center;
            h3{
                font-size: 20px;
                font-weight: 300;
                margin-bottom: 5%;
            }
            .content{
                width: 100%;
                height: 100%;
                display: flex;
                justify-content: space-around;
                align-items: center;
                .projet{
                    height: 100%;
                    width: 30%;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex-direction: column;
                    padding: 10px;
                    background-color: #e7f0ff;
                    box-shadow: 0px 5px 7px rgba(0,0,0, 0.05);
                    cursor: pointer;
                }
                img{
                    height: 70%;
                    margin-bottom: 0vh;
                }
            }
        }
    }
    @media screen and (max-width: 1000px) {
        .singleProject{
            width: 100vw;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            font-family: 'Poppins', sans-serif;
            margin-bottom: 30vh;
            button{
                position: relative;
                top: -4vh;
                left: -35%;
                width: 15vw;
                height: 4vh;
                text-transform: uppercase;
                color: white;
                background-color: #1E202B;
                border: 0;
                font-size: 14px;
                cursor: pointer;
            }
            iframe{
                width: 85%;
                height: 55vh;
            }
            .projectContent{
                margin-top: 5vh;
                width: 80%;
                display: flex;
                justify-content: center;
                align-items: center;
                text-align: center;
                flex-direction: column;
                h2{
                    font-size: 45px;
                    font-weight: 500;
                    margin-bottom: 3vh;
                }
                .desc{
                    font-size: 20px;
                    line-height: 23px;
                    margin-bottom: 3vh;
                }
                .projectInfo{
                    width: 60%;
                    display: flex;
                    justify-content: space-between;
                    font-size: 16px;
                    font-style: italic;
                    font-weight: 300;
                }
            }
            .moreProjects{
                width: 80%;
                display: flex;
                justify-content: space-around;
                height: 20vh;
                margin-top: 15vh;
                flex-direction: column;
                align-items: center;
                h3{
                    font-size: 20px;
                    font-weight: 300;
                    margin-bottom: 5%;
                }
                .content{
                    width: 100%;
                    height: 100%;
                    display: flex;
                    justify-content: space-around;
                    align-items: center;
                    .project{
                        height: 100%;
                        width: 40%;
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        flex-direction: column;
                        padding: 10px;
                        background-color: #e7f0ff;
                        box-shadow: 0px 5px 7px rgba(0,0,0, 0.05);
                        cursor: pointer;
                    }
                    img{
                        height: 70%;
                        margin-bottom: 2vh;
                    }
                }
            }
        }
    }
    @media screen and (max-width: 800px) {
        .singleProject{
            width: 100vw;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            font-family: 'Poppins', sans-serif;
            margin-bottom: 40vh;
            button{
                position: relative;
                top: -4vh;
                left: -30%;
                width: 30vw;
                height: 4vh;
                text-transform: uppercase;
                color: white;
                background-color: #1E202B;
                border: 0;
                font-size: 14px;
                cursor: pointer;
            }
            iframe{
                width: 90%;
                height: 30vh;
            }
            .projectContent{
                margin-top: 5vh;
                width: 90%;
                display: flex;
                justify-content: center;
                align-items: center;
                text-align: center;
                flex-direction: column;
                h2{
                    font-size: 20px;
                    font-weight: 500;
                    margin-bottom: 3vh;
                }
                .desc{
                    font-size: 14px;
                    line-height: 23px;
                    margin-bottom: 3vh;
                }
                .projectInfo{
                    width: 100%;
                    display: flex;
                    justify-content: space-between;
                    font-size: 12px;
                    font-style: italic;
                    font-weight: 300;
                }
            }
            .moreProjects{
                width: 100%;
                display: flex;
                justify-content: space-around;
                height: 40vh;
                margin-top: 20vh;
                flex-direction: column;
                align-items: center;
                h3{
                    z-index: 100;
                    font-size: 20px;
                    font-weight: 300;
                    margin-bottom: 20%;
                }
                .content{
                    width: 100%;
                    height: 100%;
                    display: flex;
                    justify-content: space-around;
                    align-items: center;
                    flex-direction: column;
                    .project{
                        height: 60%;
                        width: 80%;
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        flex-direction: column;
                        padding: 10px;
                        background-color: #e7f0ff;
                        margin-top: 2vh;
                        box-shadow: 0px 5px 7px rgba(0,0,0, 0.05);
                        cursor: pointer;
                    }
                    img{
                        height: 70%;
                        margin-bottom: 2vh;
                    }
                }
            }
        }
    }
</style>