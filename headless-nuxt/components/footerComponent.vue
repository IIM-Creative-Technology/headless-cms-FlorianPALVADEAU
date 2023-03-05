<template>
    <footer class="Footer">
        <a href="https://florian-palvadeau.com" class='navLink'>florian-palvadeau.com</a>
        <div class="navBar">
            <nuxtLink :to="`/contact`">Contact</nuxtLink>
            <nuxtLink :to="`/`">Home</nuxtLink>
            <nuxtLink :to="`/projects-page`">Projects</nuxtLink>
        </div>
        <div class="icons">
            <a href="https://github.com/FlorianPALVADEAU" target="_blank" rel="noreferrer"><img src="../assets/github_icon.png" alt="github_icon"/></a>
            <a href="https://www.instagram.com/flo.plvd/?hl=fr" target="_blank" rel="noreferrer"><img src="../assets/instagram_icon.png" alt="instagram_icon"/></a>
            <a href="https://www.linkedin.com/in/florian-palvadeau/" target="_blank" rel="noreferrer"><img src="../assets/linkedin_icon.png" alt="linkedin_icon"/></a>
            <a href="../assets/CV_PALVADEAU_FLORIAN.pdf" target="_blank" rel="../assets/CV_PALVADEAU_FLORIAN.pdf"><img src="../assets/cv_icon.png" alt="cv_icon" class="cv_icon"/></a>
        </div>
    </footer>
</template>

<script setup></script>

<style lang="scss" scoped>
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

    @media screen and (max-width: 1550px) {
        body{
            .Footer{
                height: 80px;
                justify-content: space-around;
                align-items: center;
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
                }
                .navBar{
                    width: 25%;
                    cursor: pointer;
                    a{
                        padding: 10px 10px;
                    }
                    a:after {    
                        height: 1px;
                        left: 50%;
                    }
                }
                .icons{
                    width: 10%;
                    height: 100%;
                }
            }
        }
    }
    @media screen and (max-width: 1370px) {
        body{
            .Footer{
                height: 80px;
                justify-content: space-around;
                align-items: center;
                a{
                    img{
                        width: 30px;
                        height: 30px;
                    }
                    .cv_icon{
                        transform: scale(1.14);
                    }
                }
                .navLink{
                    font-size: 12px;
                }
                .navBar{
                    width: 30%;
                    cursor: pointer;
                    a{
                        padding: 10px 10px;
                    }
                    a:after {    
                        height: 1px;
                        left: 50%;
                    }
                }
                .icons{
                    width: 12%;
                }
            }
        }
    }
    @media screen and (max-width: 1000px) {
        body{
            .Footer{
                height: 120px;
                justify-content: center;
                a{
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
                }
                .navBar{
                    font-size: 16px;
                    margin-left: 12vw;
                    margin-right: 12vw;
                    width: 30%;
                    a{
                        padding: 10px 10px;
                    }
                    a:after {    
                        height: 1px;
                        left: 50%;
                    }
                }
                .icons{
                    width: 14%;
                    transform: scale(0.9);
                }
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
            width: 100vw;
            .Footer{
                .navLink{ display: none; }
                .navBar{ width: 100%; }
                .icons{ display: none; }
            }
        }
    }
</style>