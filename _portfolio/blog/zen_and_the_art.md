---
title: "Zen and the Art of Documentation Maintenance"
layout: single
excerpt: "Owen Priestley"
sitemap: true
permalink: /portfolio/blog/zen/
header:
  image: zen_hero.png
sidebar:
  nav: "portfolio"
---
<h2 class="subtitle">Originally published on the Redgate blog, November 2015</h2>
<h4> </h4>
<hr>
This year's European branch of [Write The Docs](http://conf.writethedocs.org/) was kicked off in Prague by Riona MacNamara, a technical writer at Google. In her talk, _Imposter no more_, Riona suggested that many technical writers suffer from [imposter syndrome](https://en.wikipedia.org/wiki/Impostor_syndrome). The feeling that we are somehow fraudulent, and that it's only a matter of time until we're "found out".

She attributes this to the inability to attain a sense of completion. Often, a work of technical writing has no definitive finishing line. It can always be improved, re-drafted and tweaked that little bit more. An electrician can throw a switch to test a circuit, a software engineer can run unit tests. It's much harder to test words.

But does this mean we shouldn't try to test our docs?

Ongoing testing and maintenance was a recurring topic of discussion amongst speakers and attendees. As our products, services and users change, how can we make sure that the supporting documentation changes with it?

At Redgate, I work on the DLM Dashboard team with developers, testers, a UX designer and a product manager. We aim to release a new version of the product to our users every Wednesday. These frequent releases mean that our documentation is often changing and evolving.

This fast-paced release schedule isn't unusual at Redgate. Keeping our documentation up to date and relevant is a key concern for the technical communications team, particularly when some technical writers work on more than one product at once. With a growing number of products, testing and maintenance is becoming an essential part of documentation.

Some tests are strict, generally supporting only two outcomes: success or failure. Unit tests, for example, are often automatic and will only ever pass or fail. It would be practically impossible to apply this model to documentation.

[Troy Howard](https://twitter.com/thoward37) is a documentarian at Twitter and co-founder of the conference. In a lightning talk, he suggested that rather than dwelling on what our tests should be measuring, we should be measuring what we can, and using that data to diagnose our documents.

Florian Scholz and Jean-Yves Perrier, two tech writers from the Mozilla Developer Network, compared themselves to gardeners. In their talk, _Gardening open docs_, they compared their knowledge base to a network of living organisms.

So how do they maintain a [garden of over 10,000 documents](https://developer.mozilla.org/en-US/)? They set up a site to track each section of the knowledge base, indicating it's overall health based on a set of measurements:

<img src="zen-1.png" align="center">

The Mozilla Developer Network relies on this gigantic to-do list to entrust maintenance to the right people. Practical and manageable tasks are grouped into categories such as technical reviews or outdated pages. This makes it easy for their contributors to find the areas where they can help.

It's easy to take care of small details such as dead links and out-of-date screenshots. But as the scale of your documentation grows, the task of finding and fixing these elements becomes increasingly time-consuming.

Tracking documentation health, and making that data accessible, can save time and improve the quality of our documentation. The Mozilla Developer Network uses automated tests and user feedback to aggregate health scores. With a smaller knowledge base, however, it's feasible to keep track of these things manually.

Here at Redgate, some of the tech comms team have started using the project management tool [Trello](https://trello.com/) to keep track of maintenance tasks. This helps the team stay on the same page and track the overall state of the knowledge base. If somebody gets a spare half an hour, they can take a look at Trello and pick out a task.

Automating tedious processes such as checking for dead links can save a lot of time, too. [Check My Links](https://github.com/ocodia/Check-My-Links/) is a free Chrome add-on that checks a page for dead links. Valid links are highlighted in green, and any broken links in red.

<img src="zen-2.png" align="center">


We can use [Google Analytics](http://www.google.com/analytics/) to gain an insight into how users interact with our documentation. How long people spend on a page, for example, can tell us a lot about whether that document is effective or not. Ideally, users shouldn’t be staring at a quick-start guide for more than a couple of minutes.

Using readability tools such as [Hemingway Editor](http://www.hemingwayapp.com/), we can analyze the contents of a document and grade it's readability, read time and instances of the passive voice. Use these metrics to help reduce the complexity and read time of a document.

<img src="zen-3.png" align="center">

Deciding an ideal readability grade for documentation can help to ensure consistent readability across the board. Studies show that the average American reads at a tenth-grade level. Think about the audience for your docs, and how this should be reflected in readability scores.

It's clear that the role of the technical writer is changing and evolving to include a broader set of responsibilities. By using tools like these to analyse and automate our work, we can alleviate some of this responsibility, freeing up time to concentrate on collaboration and the more creative processes.