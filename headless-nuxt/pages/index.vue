<template>
    <main class="MainContent">
        <div class="aboutMe" id='aboutMe'>
            <h2>About Me.</h2>
            <p>
            I'm Florian PALVADEAU, a student at IIM school, doing my third year of
            web-development, in order to get graduated of a web-ingeneer frond-end and creative developer master.<br/><br/>

            Over the past 3 years, I have been developing many different skills, both in hardskills and in softskills. 
            I am passionate about coding, and I'm always trying to push my limits in order to learn and play with differents languages.

            My goal is to become the best web-developer that i could ever be, and I'm really determined to, maybe one day, become
            a renowned developer.<br/><br/>

            I would say that my personnality is pretty adaptative depending from a situation to another, but more generally i'm a really
            devoted person, hard-working and determined. I do not fear challenges, and always try to do my best to defeat them.<br/><br/>

            Besides, I am very social and open-minded, which i think is a pretty good advantage in the digital world,
            because it allows me to be team-spirited and to understand my working mates easier.<br/><br/>
            </p>

        </div>
        <div class="studies" id='studies'>
            <h2>My Studies.</h2>
            <p>
                Currently in the third year of my scolarship cursus, i am following a work-study program of 3 weeks working / 1 Week stodying at school.<br/>
                Thanks to my school and a part of my curiosity, i have been able to develop many hardskills in the web-development area. 
                I am able to realize a complete website from the wireframe to the development and the FTP.  In addition to this, i am very comfortable with 
                CAD and video making softwares.<br/>

                Luckily, my school is giving lessons of softskills to it's students, in order to prevent them of the embarrassing situations 
                that could happen in the professional working area, or simply in the real life. I have learnt to work in team, how to manage 
                my stress, my timetable, some angry people, and many other stuff, but also how to behave
                correctly and professionally from a situation to another.
            </p>
            <div class="cursus">
                <h3>My cursus.</h3>
                <ul class="timeline">
                    <li>
                        <div class="direction-r">
                            <div class="flag-wrapper">
                                <span class="flag">First year at IIM</span>
                                <span class="time-wrapper"><span class="time">2020-2021</span></span>
                            </div>
                            <div class="desc">
                                I learnt a lot of skills since i've been in touch with 3D softwares, Creation and Design softwares, get introduced to web 
                                development, as well as video-game programming/designing, and marketing. 
                            </div>
                        </div>
                    </li>
                    <li>
                        <div class="direction-l">
                            <div class="flag-wrapper">
                                <span class="flag">Second Year at IIM</span>
                                <span class="time-wrapper"><span class="time">2021 - 2022</span></span>
                            </div>
                            <div class="desc">
                                I decided to specialize my studies in web development. 
                                I have learnt a lot of things and web development started to become a real passion to me.
                            </div>
                        </div>
                    </li>
                    <li>
                        <div class="direction-r">
                            <div class="flag-wrapper">
                                <span class="flag">Third Year at IIM</span>
                                <span class="time-wrapper"><span class="time">2022 - 2023</span></span>
                            </div>
                            <div class="desc">
                                I started to work in companies through a work-study program, while learning on my side. I will get graduated by july of a 
                                developer project chief bachelor.
                            </div>
                        </div>
                    </li>
                    <li>
                        <div class="direction-l">
                            <div class="flag-wrapper">
                                <span class="flag">Incoming...</span>
                                <span class="time-wrapper"><span class="time">2023 - 2025</span></span>
                            </div>
                            <div class="desc">
                                2 years remaining to get graduated of a web-engeneer front-end creative developer master.
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </main>
</template>


<style lang="scss" scoped>
  $background-color: #EDF2FB;
  $border-color: #ABC4FF;
  $text-color: #1E202B;
  $text-color-lighter: #4A4E69;
  $border-color-lighter: #D3D6DA;
  .MainContent{
      width: 100%;
      height: auto;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      font-family: 'Poppins', sans-serif;
      h2{
          font-size: 40px;
          font-weight: 500;
      }
      h3{
          font-size: 30px;
          font-weight: 400;
      }
      .aboutMe, .studies{
          width: 70%;
          height: 40vh;
          font-size: 14px;
          display: flex;
          justify-content: space-around;
          flex-direction: column;
          margin-bottom: 30vh;
          margin-left: 10vw;
          p{
              margin-left: 10%;
              width: 70%;
          }
          .cursus{
              margin-left: 10%;
              width: 80%;
          }
      }
      .studies{
          height: 90vh;
      }
      .skills{
          width: 70%;
          height: 90vh;
          margin-bottom: 100vh;
          .canva{
              margin-top: 10vh;
              margin-left: 10%;
              width: 100%;
              display: flex;
              flex-direction: column;
              canvas{
                  margin-left: -10%;
                  transform: scale(0.8);
              }
          }
      }
  }

  @media screen and (max-width: 1550px) {
    body{
        .MainContent{
            h2{
                font-size: 45px;
                font-weight: 500;
            }
            h3{
                font-size: 35px;
                font-weight: 400;
            }
            .aboutMe, .studies{
                width: 70%;
                height: 50vh;
                font-size: 16px;
            }
            .studies{
                height: 120vh;
            }
            .skills{
                width: 70%;
                height: 90vh;
                margin-bottom: 80vh;
                .canva{
                    margin-top: 10vh;
                    margin-left: 10%;
                }
            }
        }
    }
  }
  @media screen and (max-width: 1370px) {
      body{
          .MainContent{
              h2{
                  font-size: 45px;
                  font-weight: 500;
              }
              h3{
                  font-size: 35px;
                  font-weight: 400;
              }
              .aboutMe, .studies{
                  width: 90%;
                  height: 50vh;
                  font-size: 16px;
                  display: flex;
                  justify-content: space-around;
                  flex-direction: column;
                  margin-bottom: 30vh;
                  margin-left: 10vw;
                  p{
                      margin-left: 10%;
                      width: 70%;
                  }
                  .cursus{
                      margin-left: 10%;
                      width: 80%;
                  }
              }
              .studies{
                  height: 120vh;
              }
              .skills{
                  width: 70%;
                  height: 90vh;
                  margin-bottom: 70vh;
                  .canva{
                      margin-top: 10vh;
                      margin-left: 10%;
                      width: 100%;
                      display: flex;
                  }
              }
          }
      }
  }
  @media screen and (max-width: 1000px) {
      body{
          .MainContent{
              h2{
                  font-size: 35px;
                  font-weight: 500;
              }
              h3{
                  font-size: 25px;
                  font-weight: 400;
              }
              .aboutMe, .studies{
                  width: 90%;
                  height: 45vh;
                  font-size: 14px;
                  margin-bottom: 20vh;
                  .cursus{
                      margin-left: 10%;
                      width: 80%;
                  }
              }
              .studies{
                  height: 100vh;
              }
              .skills{
                  width: 80%;
                  height: 90vh;
                  margin-bottom: 30vh;
                  .canva{
                      margin-top: 10vh;
                      margin-left: 10%;
                      width: 100%;
                      canvas{
                          transform: scale(0.8);
                      }
                  }
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
          .MainContent{
              .aboutMe, .studies{
                  width: 100%;
                  height: 65vh;
                  font-size: 14px;
                  margin-bottom: 20vh;
                  margin-left: 10vw;
                  .cursus{
                      h3{
                          margin-left: 10%;
                      }
                      margin-left: 5%;
                      width: 80%;
                  }
              }
              .studies{
                  height: 170vh;
                  margin-bottom: 15vh;
              }
              .skills{
                  width: 80%;
                  height: 100vh;
                  margin-bottom: 0vh;
                  .canva{
                      margin-top: 10vh;
                      margin-left: 10%;
                      width: 100%;
                      canvas{
                          margin-top: 5vh;
                          margin-bottom: 5vh;
                          margin-left: -18%;
                          transform: scale(1);
                      }
                  }
              }
          }
      }
  }

  /* ================ Timeline ================ */

  .timeline {
    position: relative;
    width: 660px;
    margin: 0 auto;
    margin-top: 20px;
    padding: 1em 0;
    list-style-type: none;
    font-family: 'Poppins', sans-serif;
  }
  .timeline:before {
    position: absolute;
    left: 50%;
    top: 7%;
    content: ' ';
    display: block;
    width: 2px;
    height: 85%;
    margin-left: -1px;
    background: #4A4E69;
    z-index: 5;
  }
  .timeline li {
    padding: 1em 0;
  } 
  .timeline li:after {
    content: "";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
  }
  .direction-l {
    position: relative;
    width: 300px;
    float: left;
    text-align: right;
  }
  .direction-r {
    position: relative;
    width: 300px;
    float: right;
  }  
  .flag-wrapper {
    position: relative;
    display: inline-block;
    
    text-align: center;
  }
  .flag {
    position: relative;
    display: inline;
    background: rgb(248,248,248);
    padding: 6px 10px;
    border-radius: 5px;
    
    font-weight: 600;
    text-align: left;
  }
  .direction-l .flag {
    -webkit-box-shadow: -1px 1px 1px $border-color, 0 0 1px $border-color;
    -moz-box-shadow: -1px 1px 1px $border-color, 0 0 1px $border-color;
    box-shadow: -1px 1px 1px $border-color, 0 0 1px $border-color;
  }
  .direction-r .flag {
    -webkit-box-shadow: 1px 1px 1px $border-color, 0 0 1px $border-color;
    -moz-box-shadow: 1px 1px 1px $border-color, 0 0 1px $border-color;
    box-shadow: 1px 1px 1px $border-color, 0 0 1px $border-color;
  }
  .direction-l .flag:before,
  .direction-r .flag:before {
    position: absolute;
    top: 50%;
    right: -39px;
    content: ' ';
    display: block;
    width: 12px;
    height: 12px;
    margin-top: -10px;
    background: #fff;
    border-radius: 10px;
    border: 3px solid $border-color;
    z-index: 10;
  }
  .direction-r .flag:before {
    left: -39px;
  }
  .direction-l .flag:after {
    content: "";
    position: absolute;
    left: 100%;
    top: 50%;
    height: 0;
    width: 0;
    margin-top: -8px;
    border: solid transparent;
    border-left-color: rgb(248,248,248);
    border-width: 8px;
    pointer-events: none;
  }
  .direction-r .flag:after {
    content: "";
    position: absolute;
    right: 100%;
    top: 50%;
    height: 0;
    width: 0;
    margin-top: -8px;
    border: solid transparent;
    border-right-color: rgb(248,248,248);
    border-width: 8px;
    pointer-events: none;
  }
  .time-wrapper {
    display: inline;
    line-height: 1em;
    font-size: 0.66666em;
    color: $text-color-lighter;
    vertical-align: middle;
  }
  .direction-l .time-wrapper {
    float: left;
  }
  .direction-r .time-wrapper {
    float: right;
  }
  .time {
    display: inline-block;
    padding: 4px 6px;
    background: rgb(248,248,248);
  }
  .desc {
    margin: 1em 0.75em 0 0;
    
    font-size: 0.77777em;
    font-style: italic;
    line-height: 1.5em;
  }
  .direction-r .desc {
    margin: 1em 0 0 0.75em;
  }
  
  /* ================ Timeline Media Queries ================ */
  
  @media screen and (max-width: 660px) { 
    .timeline {
        width: 100%;
        padding: 4em 0 1em 0;
    }
    .timeline li {
        padding: 2em 0;
    }
    .direction-l,
    .direction-r {
        float: none;
        width: 100%;
        text-align: center;
    }
    .flag-wrapper {
        text-align: center;
    }
    .flag {
        background: rgb(255,255,255);
        z-index: 15;
    }
    .direction-l .flag:before,
    .direction-r .flag:before {
        position: absolute;
        top: -30px;
        left: 51%;
        content: ' ';
        display: block;
        width: 12px;
        height: 12px;
        margin-left: -9px;
        background: #fff;
        border-radius: 10px;
        border: 2px solid $border-color;
        z-index: 10;
    }
    .direction-l .flag:after,
    .direction-r .flag:after {
        content: "";
        position: absolute;
        left: 50%;
        top: -8px;
        height: 0;
        width: 0;
        margin-left: -8px;
        border: solid transparent;
        border-bottom-color: rgb(255,255,255);
        border-width: 8px;
        pointer-events: none;
    }
    .time-wrapper {
        display: block;
        position: relative;
        margin: 8px 0 0 0;
        z-index: 14;
    }
    .direction-l .time-wrapper {
        float: none;
    }
    .direction-r .time-wrapper {
        float: none;
    }
    .desc {
        position: relative;
        margin: 1em 0 0 0;
        padding: 1em;
        background: #e0e8f7;
        z-index: 15;
    }
    .direction-l .desc,
    .direction-r .desc {
        position: relative;
        margin: 1em 1em 0 1em;
        padding: 1em;
        z-index: 15;
    }
  }
  
  @media screen and (max-width: 660px) {
    .direction-l .desc,
    .direction-r .desc {
        margin: 1em 4em 0 4em;
    }
  }
</style>