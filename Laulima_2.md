---
layout: project
type: project
image: img/calendar.png
title: "Laulima_2"
date: 2023
published: True
labels:
  - Python
  - Flask
  - HTML
  - JavaScript
  - CSS
  - Jupyter Notebook
  - Github
  - Data Analysis
  - SQLite
summary: "An improvement to Laulima while providing UH Students access to professor ratings, class insights, forums, and a calendar for all important dates."
---

<img class="img-fluid" src="../img/calendar.png">

Cotton is a horror-style text-based adventure game I developed using the functions and macros built from The Wizard's Game in [Conrad Barski's Land of Lisp](http://landoflisp.com/). Slightly more interesting and convoluted! (It is not that scary.)

Laulima is a web-based application made for UH students as a subtle upgrade to Laulima. How does it do it? We web scraped all the data from your Laulima webpage including test, quiz, and assignment dates, and imported it into a calendar where you can find all this information stored for each day. 

The idea behind Laulima_2 was to cover where our current application of Laulima lacks. Currently, you will not be notified of test or quiz due dates as you might be for assignment dates. Additionally, it can be difficult to view all your assignment dates since they appear on separate pages(no central dashboard).

Additionally to trying to solve Laulimas shortcomings, Laulima_2 intends to provide students with other useful resources. We scrape all the data from ratemyproffessor and will use it to display alongside registration screens to make registration easier. We also plan to have suggested classes for certain majors, years, prereq and such. Some additional features include a forum for school-related subjects(classes, teachers, dorms), a forum to sell items, and a syllabus reader that automatically tells you important dates (using ML), and integrated schedules with multiple students. 

This is an example of how I used flask to implement features:

@app.route('/forum', methods=['GET', 'POST'])
def forum():
   data = []
   db_path = '/Users/kawikanaweli/Desktop/Code/UHELPER/forums.db'
   db = sqlite3.connect(db_path)
   cursor = db.cursor()


   cursor.execute("SELECT * FROM forum")
   data = cursor.fetchall()
   db.close()

   form = Search()
   if(form.validate_on_submit()):
      print("searching")
   return render_template('forum.html', data=data, form=form)
