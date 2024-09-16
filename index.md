---
layout: base
title: Student Home 
description: Home Page
hide: true
---

<center><h1>Nikhil Narayan<h1>
<hr>
<h2>Welcome to MY Nighthawk page!<h2>
<hr>
<h2><p>Learn about my favorite cricket players!😁</p></h2>
<br>
<h2><button>some button text</button></h2>
<br>
<div>
<a href ="https://www.espncricinfo.com/cricketers/virat-kohli-253802">
<h2><button>Virat Kohli</button></h2>
</a>
<br>
</div>
<a href ="https://www.espncricinfo.com/cricketers/viv-richards-52812">
<div>
    <h2><button>Vivian "Viv" Richards</button></h2>

    

</div>

<h3>Guess the Number</h3>
<p>Guess a number between 1 and 10:</p>
<input type="number" id="guess" placeholder="Enter your guess">
<button onclick="checkGuess()">Check</button>
<p id="game-result"></p>

<script>
var randomNumber = Math.floor(Math.random() * 10) + 1;
function checkGuess() {
  var userGuess = document.getElementById("guess").value;
  if(userGuess == randomNumber) {
    document.getElementById("game-result").innerText = "Correct!";
  } else {
    document.getElementById("game-result").innerText = "Try again!";
  }
}
</script>


