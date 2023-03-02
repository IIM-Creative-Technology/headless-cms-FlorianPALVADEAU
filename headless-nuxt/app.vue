<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<style lang="scss">
  $background-color: #EDF2FB;
  $border-color: #ABC4FF;
  $text-color: #1E202B;
  $text-color-lighter: #4A4E69;
  ::-webkit-scrollbar {
      width: 5px;
  }
  
  ::-webkit-scrollbar-track {
      background-color: #ebebeb42;
      -webkit-border-radius: 10px;
      border-radius: 2px;
  }

  ::-webkit-scrollbar-thumb {
      -webkit-border-radius: 10px;
      border-radius: 10px;
      background: $border-color; 
  }
  body{
    transition: 0.5s ease-in-out linear; 
    font-family: 'Poppins', sans-serif;
    background-color: $background-color;
    color: $text-color;
    font-size: 16px;
    line-height: 1.5;
    width: 100vw;
    overflow-x: hidden;
    -webkit-user-select: none;  
    -moz-user-select: none;    
    -ms-user-select: none;      
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
  }
</style>