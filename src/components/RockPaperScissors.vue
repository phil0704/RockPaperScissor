<template>
    <div class="choices">
     <header>
         <h2>Make a Selection</h2>
     </header>
     <div v-if="start">
        <button @click="user = 'paper'; getComputerChoice()">Paper</button>
        <button @click="user = 'scissors'; getComputerChoice()">Scissors</button>
        <button @click="user = 'rock'; getComputerChoice()">Rock</button>
         <br>
        v.s
         <br>
         {{ computer ?  computer : 'Computer' }}
         <br>
         <div v-if="user != '' && computer != ''">
             {{ winner() }}

         </div>
     </div>
     <div v-else>
         <button @click="start = !start">Start Game</button>

     </div>
    </div>



</template>

<script>
 export default {
     name: 'RockPaperScissors',  
    data() {
         return {
             user: '',
             computer: '',
             start: false
         }
    },
     methods: {
         winner() {
             var game = this, userchoice = game.user, getComputerChoice = game.computer
             if (userchoice === getComputerChoice) {
                 return "game was a tie!";

             }
             if (userchoice === "rock") {
                 if (getComputerChoice === "paper") {
                     return "computer won!";   
                 } else {
                     return "user won!";
                 }
             }
             if (userchoice === "paper") {
                 if (getComputerChoice === "scissors") {
                     return "computer won!";
                 } else {
                     return "user won!";
                 }
             }
             if (userchoice === "scissors") {
                 if (getComputerChoice === "rock") {
                     return "computer won!";
                 }
                  else {
                     return "user won!";
                 }
             } 
         },
       
     
         startGame() {

         },
         getComputerChoice() {
             var game = this, randomNumber = Math.floor(Math.random() * 3)
             if (randomNumber === 0) {
                 game.computer = "rock";
             } else if (randomNumber === 1) {
                 game.computer = "paper";
             } else {
                 game.computer = "scissors";
             }
         }
     }

 }
</script>

<style>

</style>