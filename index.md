---
layout: base
title: Student Home 
description: Home Page
hide: true
---

<style>
  body {
    background-color: #1e1e2e;
    color: #f8f8f2;
    font-family: 'Inter', 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    margin: 0;
    padding: 0;
    background-image: 
      radial-gradient(circle at 10% 20%, rgba(189,147,249,0.03) 0%, transparent 50%),
      radial-gradient(circle at 90% 80%, rgba(189,147,249,0.03) 0%, transparent 50%);
  }
  .container {
    max-width: 100%;
    padding: 1rem 3rem;
  }
  .header {
    text-align: center;
    margin: 0 0 2rem 0;
    padding: 3rem 0 2rem;
    background: linear-gradient(180deg, rgba(45,45,58,0.7) 0%, rgba(30,30,46,0.5) 100%);
    border-bottom: 1px solid rgba(189,147,249,0.3);
    position: relative;
    overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, rgba(189,147,249,0.7), transparent);
    animation: shimmer 3s infinite;
  }
  @keyframes shimmer {
    0% { transform: translateX(-100%); }
    100% { transform: translateX(100%); }
  }
  h1 {
    font-family: Georgia, 'Times New Roman', Times, serif;
    font-size: 4.5rem;
    margin-bottom: 0.5rem;
    color: #bd93f9;
    font-weight: 500;
    text-shadow: 0 0 15px rgba(189,147,249,0.4);
  }
  h2 {
    font-size: 2rem;
    font-weight: 400;
    color: #bd93f9;
  }
  hr {
    border: none;
    height: 1px;
    background: linear-gradient(90deg, rgba(189,147,249,0) 0%, rgba(189,147,249,1) 50%, rgba(189,147,249,0) 100%);
    margin: 1.5rem auto;
    width: 60%;
  }
  .main-content {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  .nav-row {
    display: flex;
    gap: 2rem;
    width: 100%;
    justify-content: center;
  }
  .nav-section {
    background-color: #2d2d3a;
    border-radius: 12px;
    padding: 1.5rem;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    transition: all 0.3s ease;
    flex: 1;
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(189,147,249,0.1);
  }
  .nav-section::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, rgba(189,147,249,0.7), transparent);
    transition: width 0.3s ease, left 0.3s ease;
  }
  .nav-section:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.2);
    border-color: rgba(189,147,249,0.3);
  }
  .nav-section:hover::after {
    width: 90%;
    left: 5%;
  }
  .nav-table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 12px 10px;
  }
  .nav-table img {
    vertical-align: middle;
    border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    transition: all 0.3s ease;
  }
  .nav-table img:hover {
    transform: scale(1.05) rotate(3deg);
    box-shadow: 0 8px 16px rgba(0,0,0,0.3);
  }
  .nav-table a {
    color: #bd93f9;
    text-decoration: none;
    font-size: 1.2rem;
    font-weight: 500;
    transition: all 0.2s;
    display: inline-block;
    padding: 0.5rem 0.8rem;
    border-radius: 6px;
  }
  .nav-table a:hover {
    color: #ff79c6;
    background-color: rgba(189,147,249,0.1);
    transform: translateX(3px);
  }
  .cricket-section {
    text-align: center;
    padding: 3rem;
    background: linear-gradient(135deg, rgba(45,45,58,0.8) 0%, rgba(30,30,46,0.6) 100%);
    border-radius: 16px;
    box-shadow: 0 15px 30px rgba(0,0,0,0.2);
    border: 1px solid rgba(189,147,249,0.2);
    position: relative;
    overflow: hidden;
  }
  .cricket-section::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(189,147,249,0.03) 0%, transparent 50%);
    animation: rotate 20s linear infinite;
    z-index: 0;
  }
  @keyframes rotate {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
  .cricket-section h2 {
    font-size: 2.5rem;
    margin-bottom: 2rem;
    position: relative;
    z-index: 1;
  }
  .logo-image {
    width: 180px;
    height: auto;
    display: block;
    transition: transform 0.3s ease;
  }
  .sprint-image {
    width: 200px;
    height: auto;
    display: block;
    transition: transform 0.3s ease;
  }
  .button-container {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
    position: relative;
    z-index: 1;
  }
  button {
    background-color: #44475a;
    color: #f8f8f2;
    border: none;
    border-radius: 8px;
    padding: 0.8rem 1.5rem;
    font-size: 1.2rem;
    cursor: pointer;
    transition: all 0.3s;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    position: relative;
    overflow: hidden;
  }
  button::after {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 50%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  button:hover {
    background-color: #6272a4;
    transform: translateY(-3px);
    box-shadow: 0 8px 15px rgba(0,0,0,0.15);
  }
  button:hover::after {
    opacity: 1;
  }
  .controller-img {
    width: 120px;
    height: auto;
  }
</style>

<div class="container">
  <div class="header">
    <h1>Nikhil Narayan</h1>
    <hr>
    <h2>Welcome to MY Nighthawk page!</h2>
  </div>

  <div class="main-content">
    <!-- First row - Games -->
    <div class="nav-row">
      <div class="nav-section">
        <table class="nav-table">
          <tr>
            <td><img src="{{site.baseurl}}/images/gamingcontroller.jpg" class="controller-img" title="Games" alt=""></td>
            <td><a href="{{site.baseurl}}/calculator/">Calculator</a></td>
            <td><a href="{{site.baseurl}}/cookieclicker/">Cookie Clicker</a></td>
            <td><a href="{{site.baseurl}}/snakegame">Snake Game</a></td>
          </tr>
        </table>
      </div>
    </div>
    
  <!-- Second row - Jupyter -->
  <div class="nav-row">
    <div class="nav-section">
      <table class="nav-table">
        <tr>
          <td><img src="{{site.baseurl}}/images/jupyterlogo.png" class="logo-image" title="Jupyter" alt=""></td>
          <td>
            <a href="{{site.baseurl}}/problems/">Unexpected problems notebook</a><br>
            <a href="{{site.baseurl}}/python/">Python Notebook</a>
          </td>
          <td>
            <a href="{{site.baseurl}}/javascript/">Simple Javascript Notebook</a>
          </td>
          <td>
            <a href="{{site.baseurl}}/pyhack/">Python Hack Group 3.1.2</a><br>
            <a href="{{site.baseurl}}/jshack/">JS Hack Group 3.1.4</a>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <!-- Third row - Sprint -->
  <div class="nav-row">
    <div class="nav-section">
      <table class="nav-table">
        <tr>
          <td><img src="{{site.baseurl}}/images/Sprint2.png" class="sprint-image" title="Sprint" alt=""></td>
          <td>
            <a href="https://nighthawkcoders.github.io/portfolio_2025/csp/big-idea/p3/3-8-6">3.8.6 Iterating over a created list</a>
          </td>
          <td>
            <a href="https://nighthawkcoders.github.io/portfolio_2025/csp/big-idea/p3/3-8-7">3.8.7 Printing a message after iterating over a list</a>
          </td>
          <td>
            <a href="{{site.baseurl}}/jssprites/">Javascript For Loops and Sprites</a>
          </td>
        </tr>
      </table>
    </div>
  </div>
    
  <!-- Fourth row - Cricket -->
  <div class="nav-row">
    <div class="cricket-section">
      <h2>Learn about cricket!😁</h2>
      <div class="button-container">
        <a href="https://www.iplt20.com/">
          <button>The "IPL" organization</button>
        </a>
        <a href="https://www.espncricinfo.com/cricketers/virat-kohli-253802">
          <button>Virat Kohli</button>
        </a>
        <a href="https://www.espncricinfo.com/cricketers/viv-richards-52812">
          <button>Vivian "Viv" Richards</button>
        </a>
      </div>
    </div>
  </div>
  </div>
</div>