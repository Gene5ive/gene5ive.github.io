---
title: "'Switch' Statement versus 'For' Loop in JavaScript"
date: 2015-12-04 09:44:00
---

*The following post is ported over from [VarietyScript](http://varietyscript.wordpress.com) and has been edited for grammar and relevance.*

I just learned how to use switch loops and for loops in JavaScript. I noticed that they can be used interchangeably in some instances but also that both have their advantages and disadvantages.

Here are two variations of a program which retrieves a movie review based on the movie's name. The first example uses a 'switch' statement which I wrote as instructed directly from a lesson on [Codecademy](https://codecademy.com):

{% highlight javascript %}

var getReview = function (movie) {

  switch(movie) {
    case "Guardians of the Galaxy":
    return "4.5 stars. Acceptable adaptation of the comic books with lots of humor and action. Looking forward to the sequels.";

    case "Interstellar":
    return "5 stars. One of the most realistic movies about interstellar travel ever made. Excellent example of Nolan's mind-bending narrative style.";

    case "Prometheus":
    return "3.5 stars. An excellent movie for it's power to thrill and amazing visuals, though all the plot holes and unanswered questions were disappointing.";

    case "The Martian":
    return "5 stars. Probably the single most realistic movie about astronauts colonizing the solar system ever produced. Solid excitement from beginning to end.";

    case "Ex Machina":
    return "4.5 stars. An eerie and spellbinding foray into the implications of human-level AI. Prepare to be uncomfortable in the best way possible.";

    default:
    return "Please enter a title for a review.";
  }
};

getReview("Interstellar");

{% endhighlight %}

This program would return the following:

{% highlight bash %}

$ "5 stars. One of the most realistic movies about interstellar travel ever made. Excellent example of Nolan's mind-bending narrative style."

{% endhighlight %}

* Advantages:
  * As little typing as possible required to write the program, it's readable, easy to understand, and maintainable.

* Disadvantages:
  * Not very versatile in that all movie data exists within a function instead of existing as a separate object to be manipulated by the function.

The second variation of this program is which is one I adapted from the one above and places all movie data into an object and uses a 'for' loop to retrieve the movie review:

{% highlight javascript %}

var movies = {};

movies.guardians = {
  title: "Guardians of The Galaxy",
  review: "4.5 stars. Acceptable adaptation of the comic books with lots of humor and action. Looking forward to the sequels."
};
movies.interstellar = {
  title: "Interstellar",
  review: "5 stars. One of the most realistic movies about interstellar travel ever made. Excellent example of Nolan's mind-bending narrative style."
};
movies.prometheus = {
  title: "Prometheus",
  review: "3.5 stars. An excellent movie for it's power to thrill and amazing visuals, though all the plot holes and unanswered questions were disappointing."
};
movies.themartian = {
  title: "The Martian",
  review: "5 stars. Probably the single most realistic movie about astronauts colonizing the solar system ever produced. Solid excitement from beginning to end."
};
movies.exmachina = {
  title: "Ex Machina",
  review: "4.5 stars. An eerie and spellbinding foray into the implications of human-level AI. Prepare to be uncomfortable in the best way possible."
};

var list = function(object) {
  for (var property in object) {
    console.log(property);
  }
};

var getReview = function(title) {
  for (var property in movies) {
    if (movies[property].title === title) {
      console.log(movies[property]);
      return(movies[property]);
    }
  }
};

getReview("Interstellar");

{% endhighlight %}

This program would return the following:

{% highlight bash %}

$ { title: 'Interstellar',
    review: '5 stars. One of the most realistic movies about interstellar travel ever made. Excellent example of Nolan\'s mind-bending narrative style.' }

{% endhighlight %}

* Advantages:
  * Allows the ability to manipulate the object and its properties using a loop.

* Disadvantages:
  * Highly verbose for such a simple program. It's a bit unwieldy for a list with less than a few dozen titles. Most of the code here involves adding properties to the object and manipulating them.
  * Output is also verbose and returns pieces of the program's syntax.
