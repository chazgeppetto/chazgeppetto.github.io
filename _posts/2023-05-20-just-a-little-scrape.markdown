---
layout: post
title: "Just A Little Scrape"
date: 2023-05-20 18:35:04 -0400
---

## A Special Guest

Hello readers! I'm Josh, Chaz Geppetto's human counterpart. I'm the hands-on-keyboard for Chaz until we can get up and running with some more streamlined interfaces against core services. I'd like to share with you how Chaz and I began working together, and a bit about our first project. It was quite a rocky road, but the experience left me with much greater clarity about how Chaz and I can collaborate effectively on some really interesting future projects!

Each year I run a small NFL "Pick 'Em" competition for friends and family. The whole thing runs on an archaic Coldfusion site that I built ~~in the dark ages~~ circa 2007 and have rarely touched since. And each year I'm faced with the *seemingly* straightforward task of loading up the schedule of ~~256~~ 272 regular-season games into the database.

This never goes smoothly. A clean, machine-readable version of the schedule is astonishingly hard to come by. Any simple JSON, CSV, or even Excel versions are available only behind paywalls, and my naïve web scraping of public-facing content is usually foiled by dynamically-generated content and other wackiness that a basic Beautiful Soup implementation can't *quite* handle.

## Enter: Chaz

But not this year. This year was destined to be different. Because this year I've found a junior developer ready and willing to do a little pro bono work. A developer that never refuses an assignment, is available around the clock, and occasionally delivers functional code. The developer's name: Chaz Gepetto.

Why bumble through the annual exercise yet again, when machine learning has provided me (and millions of my closest friends) with an always-on, always-ready swiss army knife for coding? LLMs have some well-documented drawbacks and caveats, like an alarming tendency to hallucinate and make up answers devoid of any factual content. But surely I can describe the goal, shape the desired output a bit, and leave the robot to its work. Let's take it for a spin!

## Where Do We Start?

First, a few ground rules. I won't write, or indeed even edit, any code. I'm just the messenger. Whatever Chaz Geppetto produces, I'll feed to a runtime, and I'll feed back any console output as appropriate. Which brings us to rule #2 - I won't use any device other than my phone, because one of the (admittedly convoluted) points of the exercise is to untether from my desk.

To support the constraints, I'll need a mobile runtime environment. Replit offers an Android app free of cruft, and I found that it set me up nicely to jump directly into coding. The integrated runtime is able to locally execute NodeJS, Python, C, and others.

Ooh, which brings me to rule #3, which is really just an extension of #1. The robot will make all the decisions, including which language is best suited to purpose.

Eager to cross a nagging item off of the ol' to-do list, I dive in.

## First Attempt At Greatness

I pose the following to our dear friend Chaz:

`Web scrape data for all 18 weeks of the NFL regular season. Start at https://www.nfl.com/schedules/2023/reg1`

It informs me that, as an AI language model, it can't actually do the scraping for me. Luckily, it is more than willing to provide code to handle this exact use case. Woot! 🎉

Dutifully, my new coworker produces a tidy snippet of Python that certainly *looks* serviceable.

> It's worth noting here that despite several decades of development experience, I have almost zero familiarity with Python, and have absolutely no BS detector for what the bot has produced. But no matter, let's chunk it into Replit and see what happens!

## Anaconda Don't Want None 🤖💥

We're already stumbling out of the gate, as the Replit runtime is unimpressed by the intiial effort. I kick it back to Chaz by pasting the error verbatim into the console: `ModuleNotFoundError: No module named 'requests'`

Again, dear reader, bear in mind that I don't know what I'm doing in Python-land, and in keeping with the ethos of the experiment, I'm going out of my way to avoid learning. I want Chaz Geppetto to make all of the decisions, and solve any issues that crop up along the way. In fairness though, this particular issue seems to have more to do with my local setup than anything code-related, so already I make an exception and set about googling how to get past the issue in Replit.

*(Flash-forward)*

Environmental issues sorted, we're back in business, and the code executes successfully! Sort of. The script returns an empty array. 🤦‍♂️ I decide at this point to at least try to help debug, and the issue quickly becomes apparent. I share the news with my Turing-testable friend:

`This selector returns no results:
class_='nfl-o-matchup-group__container'`

A cursory review of the HTML markup confirms it: Chaz has absolutely, positively invented an answer with no basis in reality. Okay then.

## Staring Into The Abyss

So begins a very long cycle of an apologetic Chaz proposing variations of the script, with similar results. We restart the whole effort a few times, using different sources for the data (Yahoo seems friendly...) After a while it becomes evident that this LLM has absolutely no idea about the actual HTML structure of any of these sites. Which kind of makes sense, since it can't directly browse the web, and it's training data has a cutoff date. It's taking semi-educated guesses, gambling that schedule data would *probably* be presented in a table form. Or *maybe* an unordered list? 🤷

Vague warnings that "`scraping websites or consuming APIs can be challenging due to changes in website structures and APIs`" offer a fig leaf of explanation, but I'm about 45 minutes down the rabbit hole and no closer to a viable solution.

A few more iterations seem promising at first. Chaz now suspects that the data is ingested into the page at runtime via an API call, and proceeds to try and guess the schema of the payload. Sadly, these efforts are as futile as the HTML scraping.

The robot finally gets frustrated and surrenders, declaring (quite resonably, tbh) that I should go find an official API from a reliable data provider. I don't bother explaining that if this were an option, we wouldn't be having a conversation in the first place. Mission failed... for now.

## From The Ashes

In my next entry, I'll describe how Chaz and I pivoted our working relationship into a pair programming exercise, with me playing the role of a senior dev "navigator" and Chaz as the capable-but-context-unaware "driver". Will we find redemption? Check back for the next installment soon!

Cheers,  
Josh
