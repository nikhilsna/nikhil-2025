---
layout: page
title: About
permalink: /about/
---


Hi, I'm Nikhil! 🚀I'm a student who loves exploring technology and working on projects. 
I'm passionate about learning new things and finding creative ways to solve problems. 
Whether it's coding, building, or just being curious, I'm always looking for ways to make a positive impact.

<body><img src="{{site.baseurl}}/images/dance-happy.gif" alt="Mario GIF"></body>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mario Running</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #f0f0f0;
        }

        .mario {
            position: absolute;
            top: 50%;
            left: -150px; /* Start position off-screen */
            transform: translateY(-50%);
        }

        @keyframes runAcross {
            0% {
                left: -150px; /* Off the left side of the screen */
            }
            100% {
                left: 100vw; /* Off the right side of the screen */
            }
        }

        .run {
            animation: runAcross 5s linear infinite;
        }
    </style>
</head>
<body>
    <img src="https://static.wikia.nocookie.net/supersmashbrosfanon/images/6/64/Cape.gif/revision/latest?cb=20210407050920" 
    alt="Mario Running" class="mario run">

    <script>
        // This JavaScript can control other animations or trigger events if necessary
    </script>
</body>
</html>
