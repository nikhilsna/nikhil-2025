---
layout: post 
title: Snake Game
permalink: /snakegame/
toc: true
---

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f0f0f0;
    }

    canvas {
      border: 1px solid #000;
      background-color: #fff;
    }
  </style>
</head>
<body>

  <canvas id="gameCanvas" width="400" height="400"></canvas>

  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    const boxSize = 20; // Size of each block (20px x 20px)
    let snake = [{ x: 8 * boxSize, y: 8 * boxSize }]; // Initial position of the snake
    let food = { x: Math.floor(Math.random() * 20) * boxSize, y: Math.floor(Math.random() * 20) * boxSize }; // Random food position
    let direction = { x: 0, y: 0 }; // Initial direction of the snake
    let score = 0;

    // Listen for arrow key presses
    document.addEventListener('keydown', function (event) {
      if (event.key === 'ArrowUp' && direction.y === 0) direction = { x: 0, y: -boxSize };
      if (event.key === 'ArrowDown' && direction.y === 0) direction = { x: 0, y: boxSize };
      if (event.key === 'ArrowLeft' && direction.x === 0) direction = { x: -boxSize, y: 0 };
      if (event.key === 'ArrowRight' && direction.x === 0) direction = { x: boxSize, y: 0 };
    });

    // Main game loop
    function gameLoop() {
      // Move the snake by adding a new head
      const newHead = { x: snake[0].x + direction.x, y: snake[0].y + direction.y };
      
      // Check if the snake eats the food
      if (newHead.x === food.x && newHead.y === food.y) {
        score++;
        food = { x: Math.floor(Math.random() * 20) * boxSize, y: Math.floor(Math.random() * 20) * boxSize };
      } else {
        // Remove the last part of the snake if not eating food
        snake.pop();
      }

      // Add the new head to the snake
      snake.unshift(newHead);

      // Check for collisions with walls or itself
      if (newHead.x < 0 || newHead.y < 0 || newHead.x >= canvas.width || newHead.y >= canvas.height || snakeCollision(newHead)) {
        clearInterval(game); // Stop the game if collision occurs
        alert(`Game Over! Your score: ${score}`);
        return;
      }

      // Clear the canvas
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Draw the snake
      for (let i = 0; i < snake.length; i++) {
        ctx.fillStyle = i === 0 ? 'green' : 'darkgreen'; // Head is green, body is dark green
        ctx.fillRect(snake[i].x, snake[i].y, boxSize, boxSize);
      }

      // Draw the food
      ctx.fillStyle = 'red';
      ctx.fillRect(food.x, food.y, boxSize, boxSize);
    }

    // Check if the snake collides with itself
    function snakeCollision(head) {
      for (let i = 1; i < snake.length; i++) {
        if (head.x === snake[i].x && head.y === snake[i].y) {
          return true;
        }
      }
      return false;
    }

    // Run the game loop every 100 milliseconds
    const game = setInterval(gameLoop, 100);
  </script>

</body>
</html>
