<template>
    <div class="Contact" data-barba="container" data-barba-namespace="wipe">
      <div class="contact_content">
        <h2 class='h2Contact'>Contact Me.</h2>
        <form id="formContact">
          <label>Name</label>
          <input type="text" name="user_name" placeholder='Frédéric Mousseau'/>
          <label>Email</label>
          <input type="email" name="user_email" placeholder='frederic.mousseau@gmail.com'/>
          <label>Message</label>
          <textarea name="user_message" placeholder='Your message here...'/>
          <input type="hidden" name="from_name" value='Florian'/>
          <input type="submit" value="Send" />
        </form>
        <div id="moreInfoContact" class="adress">
            <h2>GET IN TOUCH.</h2>
            <p>ADDRESS</p>
            <p>Florian Palvadeau</p>
            <p>105 rue de la brèche-du-houx - 78760</p>
            <p>France, EU</p>
            <p>06-52-26-60-54</p>
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
    .contact_content{
        font-family: 'Poppins', sans-serif;
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        margin-bottom: 15vh;
        .h2Contact{
            font-size: 40px;
            font-weight: 500;
            width: 70%;
            display: flex;
            justify-content: flex-start;
            margin-left: -35vw;
            margin-bottom: 15vh;
        }
        form{
            width: 100%;
            height: 50%;
            display: flex;
            justify-content: space-around;
            flex-direction: column;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
  
            input, textarea{
                border-radius: 5px;
                border: 0;
                resize: none;
                margin-top: -3%;
                padding-left: 10px;
                padding-right: 10px;
                color: #4A4E69;
                &:focus{
                    outline: none !important;
                }
            }
            textarea{
                padding-top: 10px;
                padding-bottom: 10px;
            }
            input{
                height: 8%;
            }
            input[type="submit"]{
                margin-top: 0%;
                background-color: #dce7ff;
                cursor: pointer;
                &:hover{
                    background-color: #c0d4fd;
                }
            }
        }
        .adress{
            width: 100%;
            height: 40%;
            display: flex;
            justify-content: flex-end;
            align-items: center;
            flex-direction: column;
            margin-bottom: -5%;
            h2{
                margin-bottom: 5%;
                font-size: 26px;
            }
            p{
                font-size: 16px;
                line-height: 25px;
            }
        }
    }
    @media screen and (max-width: 800px) {
      html, body{
          box-sizing: border-box;
          overflow-x: hidden;
          -webkit-box-sizing: border-box;
          -moz-box-sizing: border-box;
      }
      body{
        .contact_content{
            width: 100%;
            height: 120vh;
            margin-bottom: 20vh;
            .h2Contact{
                font-size: 30px;
                width: 70%;
                margin-bottom: 5vh;
            }
            form{
                width: 80%;
                padding: 20px;
                height: 40%;
                margin-top: -10vh;
                input, textarea{
                    margin-top: 0%;
                }
                ::placeholder{
                    font-size: 12px;
                }
            }
            .adress{
                margin-top: -25vh;
                height: 40%;
                h2{
                    margin-bottom: 5%;
                    font-size: 18px;
                }
                p{
                    font-size: 12px;
                    line-height: 25px;
                }
            }
        }
      }
    }
  </style>