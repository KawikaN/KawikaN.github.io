---
layout: project
type: project
image: img/vacay/vacay-square.png
title: "WikiToConfluence"
date: 2024
published: true
labels:
  - Python
  - Meta Llama
  - SQL
  - Gitlab
summary: "A project for the Gemini observatories of Noirlab to categorize and save their document archive online."
---

<img class="img-fluid" src="../img/vacay/vacay-home-page.png">

This project is a script that I created as an Intern while working on Hawai'i island for Noirlab. This project impacted over 300 Noirlab staff in everyday duties.

The script was primarily written in Python and utilizes multiple API calls to various software. It requires access to the internal document archive that is saved within an SQL database and displayed as a wiki page. I was able to write a script that parsed the necessary data from the SQL data format. This data needed to be filtered since it was not exported in one universal format. We saw files that were written in HTML, plain text, embedded images, and much more. After converting all the files document to plain text and under a universal format I had to save the photos into a folder and the position in text that they were found. These photos were made up of many formats so I had to ensure I captured all possible photo formats(PDF, PNG, jpeg...). I replaced the position in the text where the photo is with brackets and the name of the associated file. Ex. [GeminiSouthLaserDiagram1]. Following this was probably the most difficult part of the project. I wrote an algorithm that categorized all the files into relevant topics. This was trivial because the SQL database was not designed with categories of files, instead it had nested links (think of a Wikipedia page). Thus, I had arbitrary file names and content that right now were not connected to one another but built off of each other. 

The format of the file names also came in various formats. Some contained the topic, location, or acronyms. Because I was trying to make an inference on what the content within the file was on I had ot keep in mind the formatting of the file. This meant that I arranged an array with various phrases that I did not want the algorithm taking into consideration when grouping. Some examples: North, South, Meeting, First. 

Following this, I also set up an array that allowed us to exclude files we no longer wanted. Ex. APKMeeting_Notes(if this phrase is found within any file in any spot it will not save the file to the final dictionary that we will push to confluence). On the same note, there is an array for file categories we expect to find and want to be sure to save. This means that if the file happens to fit another category but we explicitly stated that we wanted files under this category it will be saved to the category we explicitly stated. 

The algorithm will loop over all the files we have pulled from the SQL database. It will then loop over the indexes of each title and compare it to the same index of the next page title. If there exists multiple indexes within the word that match (at least 3 lowercase letters) then we will assume this is a valid prefix and save it to a prefix dictionary where the characters are the key and the names of the files that share that prefix are the value. A specific case we also looked for was any filename with a _. If we come across an "_" we assume that everything before that would create a prefix. For example: MainMirror_. 

Now in the case that there were no shared prefixes found using the previous method between the words we will try to check for matching capitalized letters within the word. This actually runs "asynchronously" with the previous check (runs first check for the first characters then second). If there are at least 2 capitalized letters that match we keep going til we find the first lowercase letter and assume this is a prefix. Ex. ABk => prefix = "AB". 

Finally, if neither of the checks worked we will resort to our last case. Here we check if 2 characters match (this is less accurate since it is very possible that two words share 2 similar letters but not the same category). 

If the two titles we are checking did not fall into any case it will be saved under a special list for those with no found Categories. 

After we have the files categorized we will then connect to the confluence API. Here we will create files with the title being the file name and the content being our parsed & filtered file content associated with it. Here we also have to import our images back to replace the placeholders we set earlier. After this, we publish all the files. 

In one of the final steps, we will again use the confluence API to create the folders that with the category names at the title. We will then move all of our filled files under those categories.

In this project I gained experience with utilizing API's, inspecting SQL databases and breaking down difficult problems into easier subproblems within a single project. 

Here is some example code to illustrate Simple Schema use:

{% gist 9defa1fb3f4eb593ba5fa9eacedca960 %}
 
Source: <a href="https://github.com/theVacay/vacay">theVacay/vacay</a>
