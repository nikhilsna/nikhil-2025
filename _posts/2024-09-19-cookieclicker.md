---
layout: post 
title: Cookie Clicker
permalink: /cookieclicker/
toc: true
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 50px;
      background-color: #f7f7f7;
    }

    #cookie {
      width: 150px;
      cursor: pointer;
      transition: transform 0.1s;
    }

    #cookie:active {
      transform: scale(0.9);
    }

    #counter {
      font-size: 2em;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <img id="cookie" src="{{site.baseurl}}/images/cookie.png" alt="Cookie">
  <div id="counter">Cookies: 0</div>

  <script>
    let cookieCount = 0;

    const cookie = document.getElementById('cookie');
    const counter = document.getElementById('counter');

    cookie.addEventListener('click', function() {
      cookieCount++;
      counter.textContent = `Cookies: ${cookieCount}`;
    });
  </script>

</body>
</html>
