<template>
    <footer className="Footer">
        <nuxtLink :to="`/`" className='navLink'>florian-palvadeau.com</nuxtLink>
        <div className="navBar">
            <nuxtLink :to="`/contact`">Contact</nuxtLink>
            <nuxtLink :to="`/`">Home</nuxtLink>
            <nuxtLink :to="`/projets`">Projects</nuxtLink>
        </div>
        <div className="icons">
            <nuxtLink :to="`https://github.com/FlorianPALVADEAU`" target="_blank" rel="noreferrer"><img src="../assets/github_icon.png" alt="github_icon"/></nuxtLink>
            <nuxtLink :to="`https://www.instagram.com/flo.plvd/?hl=fr`" target="_blank" rel="noreferrer"><img src="../assets/instagram_icon.png" alt="instagram_icon"/></nuxtLink>
            <nuxtLink :to="`https://www.linkedin.com/in/florian-palvadeau/`" target="_blank" rel="noreferrer"><img src="../assets/linkedin_icon.png" alt="linkedin_icon"/></nuxtLink>
            <nuxtLink :to="`#`" target="_blank" rel="../assets/CV_PALVADEAU_FLORIAN.pdf"><img src="../assets/cv_icon.png" alt="cv_icon" className="cv_icon"/></nuxtLink>
        </div>
    </footer>
</template>

<script setup></script>

<style scoped lang="scss">
    $background-color: #EDF2FB;
    $border-color: #ABC4FF;
    $text-color: #1E202B;
    $text-color-lighter: #4A4E69;
    .Footer{
        font-family: 'Poppins', sans-serif;
        background-color: $background-color;
        color: $text-color;
        width: 100vw;
        height: 80px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        font-size: 16px;
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        box-shadow: 0px -3px 6px rgba(0,0,0, 0.2);
        z-index: 100;
        a{
            color: $text-color;
            text-decoration: none;
            img{
                width: 30px;
                height: 30px;
            }
            .cv_icon{
                transform: scale(1.14);
            }
        }
        .navLink{
            font-size: 14px;
            width: 10%;
        }
        .navBar{
            width: 20%;
            height: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: 0.3s ease linear;
            cursor: pointer;
            a{
                color: $text-color;
                text-decoration: none;
                letter-spacing: 0.05em;
                
                display: inline-block;
                padding: 10px 10px;
                position: relative;
            }
            a:after {    
                background: none repeat scroll 0 0 transparent;
                bottom: 0;
                content: "";
                display: block;
                height: 1px;
                left: 50%;
                position: absolute;
                background: $text-color-lighter;
                transition: width 0.3s ease 0s, left 0.3s ease 0s;
                width: 0;
              }
            a:hover:after, a.selected:after {
                width: 100%; 
                left: 0; 
            }
        }
        .icons{
            width: 10%;
            height: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: nowrap;
        }
    }
</style>