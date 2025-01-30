---
layout: project
type: project
image: /img/wdl.png
title: "HawaiianWordle"
date: 2024
published: true
labels:
  - Python
  - JavaScript
  - HTML
  - CSS
  - Flask
summary: "Wordle for those who intend to learn more Hawaiian. It also has my own additions to it that doesn't make it identical to NYT's infamous wordle.."
---

<img class="img-fluid" src="../wiki.png">

This project intends to perpetuate the Hawaiian language by gamifying the learning process. This is done through the recently popular Wordle game. 

This project has an emphasis on web scrapping. This is because I utilized Python to web-scrape the definitions of words from https://wehewehe.org/. 

Additionally, I used a Flask framework in order to have my Python data easily displayed via JS on different web pages. The choice of Flask was because I wanted something that was centered towards smaller projects with less setup and allowed me to pass data from Python to JS/HTML. 

JavaScript covered most of the front-end code since it gave the simple GUI of Wordle and also handled the processing of whether each letter/word was correct or incorrect and displayed as such. 

I have an array that stores all the possible words that may be used for the "Word of the day" but I decided to have it randomly picked on the Python side within the flask app rather than on the Javascript side which would have made it easier to implement in the front-end. Although this made it more difficult to pass the data between one another while keeping it global and up to date with all aspects it allowed me to use python on the final screen to web scrape the definition for the user to see and read. 

The last important feature of this project which differs from other Wordle applications is you are able to click on any word within the definition of the word of the day and be able to get the definition of that word as well. 
