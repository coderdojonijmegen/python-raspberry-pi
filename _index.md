---
title: "Python - Raspberry Pi"
date: 2026-06-05T20:53:27+02:00
draft: false
toc: true
headercolor: "teal-background"
onderwerp: Python
layout: single
---
Een Raspberry Pi is een mini-computer waar je allerlei leuke dingen mee kunt doen. 
Je kan de Raspberry Pi als computer gebruiken.
Daarnaast kun je er ook allerlei apparaatjes en elektronische schakelingen aan koppelen.

We gaan met bewegingssensoren, afstandssensoren en een stappenmotor aan de slag. 

<!--more-->
  <script src="/instructies/python-raspberry-pi/main.js"></script>

  <style>
    /* Matrix Background */
    .background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgb(255, 255, 255);
      filter: blur(3px);
      z-index: -1;
    }

    .letter {
      position: absolute;
      font-size: 20px;
      color: var(--matrix-color, rgba(0, 255, 0, 0.8));
      animation: fall linear infinite;
    }

    @keyframes fall {
      0% {
        transform: translateY(-100vh);
        opacity: 0;
      }

      10% {
        opacity: 1;
      }

      90% {
        opacity: 1;
      }

      100% {
        transform: translateY(100vh);
        opacity: 0;
      }
    }

    /* Example Elm button */
    #colorButton {
      position: fixed;
      top: 20px;
      left: 20px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      background-color: #222;
      color: #0f0;
      border: 1px solid #0f0;
      border-radius: 5px;
      z-index: 10;
    }

    .s.sb {
        overflow: unset !important;
    }
  </style>

  <!-- <script> // Ask before reload
    window.onbeforeunload = function (e) {
      e = e || window.event;
      if (e) {
        e.returnValue = 'Sure?';
      } return 'Sure?';
    }; </script> -->

  <div id="myapp"></div>

  <script>
    // Initialize Elm
    var app = Elm.Main.init({
      node: document.getElementById('myapp')
    });

    // Subscribe to Elm port for color changes
    app.ports.changeLetterColor.subscribe(function (color) {
      document.documentElement.style.setProperty('--matrix-color', color);
    });
  </script>

Mocht het zo niet lukken, dan kun je nog [hier](instructie/) kijken.
