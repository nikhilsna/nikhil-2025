---
layout: post 
title: Calculator
permalink: /calculator/
toc: true
comment: true
---

<script src="https://utteranc.es/client.js"
        repo="nikhil-2025"
        issue-term="pathname"
        theme="github-dark"
        crossorigin="anonymous"
        async>
</script>

  <center><title>Calculator Project</title></center>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f0f0f0;
      margin: 0;
    }
    .calculator {
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
    }
    #display {
      width: 100%;
      height: 50px;
      font-size: 24px;
      text-align: right;
      padding: 10px;
      margin-bottom: 10px;
      border: none;
      background-color: #e0e0e0;
      border-radius: 5px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }
    button {
      padding: 20px;
      font-size: 18px;
      border: none;
      background-color: #6FC276;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #ccc;
    }
  </style>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled />
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="appendNumber('/')">/</button>
      <button onclick="appendNumber('*')">*</button>
      <button onclick="backspace()">&#x2190;</button>
      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button onclick="appendNumber('-')">-</button>
      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button onclick="appendNumber('+')">+</button>
      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button onclick="calculate()">=</button>
      <button onclick="appendNumber('0')" style="grid-column: span 2;">0</button>
      <button onclick="appendNumber('.')">.</button>
    </div>
  </div>

  <script>
    function clearDisplay() {
      document.getElementById('display').value = '';
    }

    function appendNumber(number) {
      document.getElementById('display').value += number;
    }

    function backspace() {
      let display = document.getElementById('display').value;
      document.getElementById('display').value = display.slice(0, -1);
    }

    function calculate() {
      let display = document.getElementById('display').value;
      try {
        document.getElementById('display').value = eval(display);
      } catch (error) {
        document.getElementById('display').value = 'Error';
      }
    }
  </script>
</body>
