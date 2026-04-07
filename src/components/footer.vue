<template>
    <footer>
      <p>Feeter</p>
      <p>Touch 'em</p>
      <div class="toes"> 
        <div class="left toeBox">
          <div class="pinkey"></div>
          <div class="forth"></div>          
          <div class="thrid"></div>          
          <div class="second"></div> 
          <div class="big"></div>
        </div>
        <div class="right toeBox">
          <a class="toeLink" href="https://github.com/BlueCalculator" target="_blank" rel="noopener noreferrer">
            <div class="big"></div>
          </a>
          <div class="second"></div>          
          <div class="thrid"></div>          
          <div class="forth"></div>          
          <div class="pinkey"></div>
        </div>        
      </div>
    </footer>
</template>

<style scoped>
    footer {
        width: 100vw;
        height: 180px;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        border-top: 1px solid var(--solidLine);
    }    
    .toes{
      display: flex;
      align-items: center;
      flex-direction: row;
      gap: -230px;
    }
    .toeBox{
      display: flex;
      flex-direction: row;
      align-items: baseline;
      gap: 2px;
    }
    .toeLink{
      text-decoration: none;
      color: black;
    }
    .right::after{
      content: '';
      width: 230px;
      height: 0;
      border-bottom: 60px solid peachpuff;
      border-left: 50px solid transparent;
      border-right: 180px solid transparent;
      border-top: 0px solid transparent;
      width: 100px;
      bottom: 0;
      position: absolute;
    }
    .left{
      position: relative;
      margin-right: 10px;
    }
    .right{
      position: relative;
    }
    .left::after{
      position: absolute;
      content: '';
      width: 230px;
      height: 0;
      border-bottom: 60px solid peachpuff;
      border-left: 180px solid transparent;
      border-right: 50px solid transparent;
      border-top: 0px solid transparent;
      width: 100px;
      bottom: 0;
    }
    .big{
      position: relative;
      background-color: peachpuff;
      width: 60px;
      height: 120px;
      border-radius: 25px 25px 0 0;
      box-shadow: 0 -4px 10px 2px rgba(0,0,0,0.05);
    }
    .big::after{
      content: '';
      position: absolute;
      background-color: rgb(255, 233, 213);
      display: block;
      width: 50px;
      height: 40px;
      border-radius: 28px 28px 40px 35px;
      transform: translate(10%, 20%);
      transition: .5s;
      box-shadow: inset 0px -5px 4px 0px rgb(252, 219, 191);
    }
    .big:hover::after {
      content: "Github";
      transform: scale(1.1) translate(10%, 10%);
    }
    .second{
      position: relative;
      background-color: peachpuff;
      width: 40px;
      height: 130px;
      border-radius: 15px 15px 0 0;
      box-shadow: 0 -4px 10px 2px rgba(0,0,0,0.05);
    }
    .second::after{
      content: '';
      background-color: rgb(255, 233, 213);
      display: block;
      width: 33px;
      height: 30px;
      border-radius: 28px 28px 40px 35px;
      transform: translate(10%, 20%);
      box-shadow: inset 0px -2px 4px 0px rgb(252, 219, 191);
    }
    .thrid{
      position: relative;
      background-color: peachpuff;
      width: 40px;
      height: 105px;
      border-radius: 15px 15px 0 0;
      box-shadow: 0 -4px 10px 2px rgba(0,0,0,0.05);
    }
    .thrid::after{
      content: '';
      background-color: rgb(255, 233, 213);
      display: block;
      width: 33px;
      height: 30px;
      border-radius: 28px 28px 40px 35px;
      transform: translate(10%, 20%);
      box-shadow: inset 0px -2px 4px 0px rgb(252, 219, 191);
    }
    .forth{
      position: relative;
      background-color: peachpuff;
      width: 40px;
      height: 75px;
      border-radius: 15px 15px 0 0;
      box-shadow: 0 -4px 10px 2px rgba(0,0,0,0.05);
    }
    .forth::after{
      content: '';
      background-color: rgb(255, 233, 213);
      display: block;
      width: 33px;
      height: 30px;
      border-radius: 28px 28px 30px 35px;
      transform: translate(10%, 20%);
      box-shadow: inset 0px -2px 4px 0px rgb(252, 219, 191);
    }
    .pinkey{
      position: relative;
      background-color: peachpuff;
      width: 40px;
      height: 45px;
      border-radius: 15px 15px 0 0;
      box-shadow: 0 -4px 10px 2px rgba(0,0,0,0.05);
    }
    .pinkey::after{
      content: '';
      background-color: rgb(255, 233, 213);
      display: block;
      width: 33px;
      height: 22px;
      border-radius: 38px 38px 40px 35px;
      transform: translate(10%, 20%);
      box-shadow: inset 0px -2px 4px 0px rgb(252, 219, 191);
    }

    @media (max-width: 480px) {
      .left{
        display: none;
      }
    }
</style>