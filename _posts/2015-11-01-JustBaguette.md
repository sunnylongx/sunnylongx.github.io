---
layout: post
title:  "Just Baguette"
image: ''
date:   2015-11-01 00:00:01
tags:
- startup
- machine learning
description: 'Just Baguette - Grocery shopping re-imagined'
categories:
- startup
---

In January of 2015, I started working on a new startup called Just Baguette, which is a bad play on words for: Just Bag It - like a grocery store...We started as a way for people to better know their weekly shopping duties - recall the many moments of: "Oops, do I still have milk at home?" We planned to create a back-end machine learning algorithm that could produce personalized grocery lists for customers. It was a genuine problem, but not enough to base a whole product out of. 

One of the most memorable discussions with a friend about product-market fit resulted in a key learning: A new product will only take hold if it is life or death or if it so easily fits into our daily routine and brings with it an even greater ease or efficiency. Our idea was neither a matter of life/death (so what if I don't have milk for a week?) and it wasn't super easy to incorporate into someone's weekly regiment. So we improved it. 

Not only would we provide a weekly grocery list for you, but we would go the whole nine yards - we would go buy it for you and deliver it. At the time, there were more grocery/food delivery startups (remember "uber for X"?) than I could keep track of - but they all suffered a crippling problem - groceries spoil. Without the recipient at home, the food would go bad, unless extra money was spent on packaging (Blue Apron). We decided to further differentiate ourselves by directly partnering with apartments and allowing residents to choose for us to deliver directly into their fridge. In the age of airBNB, what's another stranger entering your apartment?

Let me recap:
* Weekly email with grocery list of recommended items.
* Add/delete (pair recipes and automatically add the ingredients to cart)
* Get groceries delivered (even direclty into your kitchen/fridge)

We wanted to create the kitchen of the future - one that was always stocked with what you wanted, when you wanted. As a further angle - we wanted to cut down on waste - by learning a consumer's habits, we could prescribe the perfect amount of food.

I had the chance to work with a fantastic group of people - two fellow MIT 2013 graduates as cofounders and 5 MIT students (5 developers, 1 UI/UX, and myself)

In only a couple months, we built out am amazing prototype (web app and iOS app):

<img src="/assets/img/JustBaguette/searchBar.png" width="700px" alt="Just Baguette Interface">

<img src="/assets/img/JustBaguette/RecipesExpanded.png" width="700px" alt="Just Baguette Recipes View">

<img src="/assets/img/JustBaguette/iOS.png" width="300px" alt="Just Baguette iOS Interface">

A small snippet of my code for a simple collaborative filter:

{% highlight python %}
for item_one in item_list:
	item_array = []
	for item_two in item_list:
		if item_one == item_two:
			pass
		else:
			item_array.append((grocery_names[item_two],angle(item_vectors[item_one],item_vectors[item_two])))
	final_recs[grocery_names[item_one]]=sorted(item_array, key=lambda tup: tup[1])[:3]
{% endhighlight %}


With the client side ready to go, we partnered with a few local apartment complexes around the area to offer our service for free as a pilot test. The unit economics worked out to be breakeven if we could deliver to 8 people for each trip to the grocery store.

Commence marketing! I established partnerships with the local apartment complexes (300 plus units per complex) and gave out cards to residents as they passed through the lobby. Here were some of the ones we designed:

<img src="/assets/img/JustBaguette/JBCardWatermark1.png" width="700px" alt="Just Baguette Card Overhead">

<img src="/assets/img/JustBaguette/JBCardWatermark2.png" width="700px" alt="Just Baguette Card Travel">

<img src="/assets/img/JustBaguette/JBCardWatermark3.png" width="400px" alt="Just Baguette Card Fridge">

Soon, we were making two trips per week to the grocery store and had a small cadre of users (across apartment residents as well as students living on campus). One problem that kept plaguing us was that despite us offering free delivery, our customers would oftentimes forget to place their orders before our cutoff - despite notifications and reminders. We decided that with a few more adjustments, we could frame our offering more in terms of a smart fridge - sensors in and around the fridge to make sure food was always ordered. Almost like an Amazon Dash, but automatic and smarter. However, before we explore further into this model, it was already September - and my amazing team of MIT students were headed back to school - which brought me to a crossroad of how to proceed...

In the end I decided to shutter the project - having expanded the original scope twice, I'm not sure the last pivot would have gotten us to the right traction amount. Despite the unfortunate ending - the journey of taking an idea to product was one of the most educational experience. Things learned:
* Team management, product management
* ML and cool algorithms
* Marketing and business development
* Customer Feedback
* Strategy and product development

[We even ended up with some great press](http://bostinno.streetwise.co/all-series/boston-grocery-delivery-service-mit-startup-just-baguette/)

