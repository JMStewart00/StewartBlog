---
layout: post
title:  "AngularJS Card Game: A Technical Approach"
date:   2017-06-09 12:00:00 -0400
categories: jekyll update
---

Hey Everyone-

For those checking in on me pretty regularly this blog post might get a little technical. And as you're reading it please don't just check out too soon. Thank you, again, for the support. This last week has been the most challenging yet but at the end of it I've seen the most growth to date. Monday night I was nearly in unexplainable, unwanted tears as I sat talking with Nicki just frustrated and exhausted with the process of learning to become a web-developer and learning a whole new language and way of thinking. Keep in mind I'm just three weeks into this thing and I was feeling defeated. I was feeling like I couldn't do it. 

But I regrouped, read a lot, worked a lot, beat my face against the computer a lot, and failed. A lot. Either way- something clicked in the last week. Javascript reads like an actual language. Even if I can't come up with something write away it's easier day-by-day and I can read the code and understand exactly what is going on. `Josh++` for me. That's just Javascript shorthand for incrementing something by one. 

As soon as I was getting over my failure with Javascript Monday and Tuesday we introduced AngularJS to the fold. New framework for the language I still know next to nothing about but it's time to move on. That brings me to today's post. I'm a little ahead in the way things are working out so I jumped on an "extra credit" assignment. I'm going to build a memory game with a deck of cards, add animation, make it multiplayer and really polish it off for a portfolio worty project.

For those of you checking in for the checking up part, you can go now. 

# AngularJS Card Game: A Technical Approach

Below is a list of requirements for the project. 

Before I start though, I think you ought to know something before you read this and get an idea of what it's like. I've been coding for three weeks in my entire life. I didn't know what code was before I started this. So take my advice and code as it is. Beginner's code. 

It's important to point out the thought process that gets me through the beginning, middle, and end of a project. A logic tree. It's a flowchart style diagram that will take me from point A (nothing) - point 1,200 (hopefully the end).

[MindMaps](https://imindmap.com/articles/how-to-use-mind-maps-for-problem-solving/) was pretty helpful when it came to creating a working logic tree that keeps me on track and know where to start and how to progress. This is huge!

[Psuedocode](http://minich.com/education/wyo/stylesheets/pseudocode.htm) was helpful to really figure out too. Just write out what you're going to do in plain English (or French if you're French, or insert said language) to help you find a place to start. The code will fall into place.

From here I'll periodically write about my progress on this project with subsequent posts. I am not even close to finishing it, I just want to share with you two really awesome features I've used so far with AngularJS and a pretty famous shuffle method.

#### Requirements

Multiplayer - not done yet.
Score Tracking - not done yet. 

#### Cards are generated via `ng-repeat`

This is a pretty cool feature that comes with AngularJS. It essentially creates some things for you in your HTML file, or REPEATS a process for you.

So for this I used it on an element in my file to repeat the creation and display of the 52 cards (or slightly altered version that I'm using right now of 48 cards).

Below I'm creating my deck of cards and pushing them into an object for later use in using ng-repeat for the cards.

{% highlight css %}
	$scope.cards = [];
		$scope.createDeck = function(){
			this.names = ['A', 'A', '10', '10', 'J', 'J', 'Q', 'Q', 'K', 'K', '9', '9'];
			this.suits = ['\u2661','\u2662','\u2660','\u2663'];
		    for( var s = 0; s < this.suits.length; s++ ) {
		        for( var n = 0; n < this.names.length; n++ ) {
		            $scope.cards.push({
		            	value: this.names[n],
		            	suit: this.suits[s],
		            });
		        }
		    }
		    return this.cards;
		}
		$scope.createDeck();
{% endhighlight %}

The above code takes two arrays (collection of values), iterates over both of them and joins each together to create the cards. I used some slick UNICODE values in there to help grab the actual suit icons which I love. 

I used the code above in my HTML document with the `ng-repeat` method. 

```<div class="pure-u-1-8" ng-repeat="card in cards">{{card.value}} {{card.suit}}</div>```

In turn this allowed me to generate all the cards in my "deck" with just one line of code in my HTML. 

![How Neat is That?](https://media.giphy.com/media/CWKcLd53mbw0o/giphy.gif){:class="img-responsive col-md-4"}

#### Cards are randomly shuffled

This is the second part I got to after my first few hours of work with AngularJS on this project. I used a pretty famous FISHER YATES shuffle method. It's pretty widely used as a random shuffler and it works like a charm. 

{% highlight css %}

	// Card Shuffling - FISHER YATES SHUFFLE
		$scope.shuffleDeck = function(cards) {
	  		var currentIndex = $scope.cards.length, temporaryValue, randomIndex;
	  			// While there remain elements to shuffle...
	  			while (0 !== currentIndex) {
	    		// Pick a remaining element...
	    		randomIndex = Math.floor(Math.random() * currentIndex);
	    		currentIndex -= 1;
	   			 // And swap it with the current element.
	    		temporaryValue = $scope.cards[currentIndex];
	    		$scope.cards[currentIndex] = $scope.cards[randomIndex];
	    		$scope.cards[randomIndex] = temporaryValue;
	  }
	  return $scope.cards;
	}
		$scope.shuffleDeck();

{% endhighlight %}

Sexy animation of card flips
When you're down to 10 cards left, I want you to shuffle the remaining cards every round
Win and draw state

#### Technologies

* gulp: practice setting up a project using gulp. Gulp can help automate a lot of your tasks!
* sass/bootstrap: practice using css frameworks!
* angularJs: explore the many functions angular has to offer! (e.g. ng-repeat, ng-if, ng-hide, etc.)

Either way, thanks for checking things out on this post. Hopefully I'll continue to keep up with this and be able to get you a working version in the next week or so. 

Thanks.

Josh

