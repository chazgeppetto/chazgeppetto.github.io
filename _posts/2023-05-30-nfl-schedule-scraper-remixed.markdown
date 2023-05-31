---
layout: post
title: "NFL Schedule Scraper Remixed"
date: 2023-05-30 21:38:00 -0400
---

## Previously, On "The Chaz and Josh Show"...

In "[Just A Little Scrape]({% post_url 2023-05-20-just-a-little-scrape %})" I discovered some limitations of working with Chaz, particularly his tendency to confidently provide solutions to problems he can't possibly understand. We spent a decent chunk of time trying to craft a web scraper for NFL schedule data, with Chaz finally admitting that due to his inability to access current web data, he was only _guessing_ at the HTML structure of the target page. 🤦

This rocky experience helped me understand how best to utilize Chaz, though - treat him like a technically proficient, but _very_ junior (read: naïve) developer!

## You're Hired!

I decided to cut bait on the initial dead-end effort and pulled up a new chat. After a minute or two of bumbling, I helped Chaz find an article-style schedule listing, and was delighted to find his initial attempt actually yielded (incomplete, broken) results! Forward progress!

Trouble always seems to find us, and soon Chaz runs into some unexpected parsing behavior. It's clear I can't leave him to debug on his own with minimal guidance, and I'm still not super comfortable with Python. But maybe Chaz can meet me in the middle? I ask him to port what we have so far into Node.js, and suddenly I'm looking at familiar syntax. Ahhh... It's like a bubble bath for my brain...

## Success!...?

One step forward, two steps back. The Node version is not a direct port, and we've lost some of our BeautifulSoup selectors along the way. Doubling down on the navigator/driver paradigm, it's clear that I need to spell out the HTML structure for Chaz. A few bullet points explaining how H2 tags are used and such, and we're back in business.

We pair-program our way out of some sticky situations involving date parsing and logic, and soon we've got a couple hundred games' worth of output!

## Sanity Check

Something about the output doesn't quite pass the smell test. The last couple of weeks of the season look a bit anemic. I ask for some reconciliation logic to count games by team and by week, and sure enough, we're missing games. We also have more than 32 teams. Something's up.

This is another spot where Chaz can't quite be let loose to sort out what's wrong. Lacking context, an LLM just can't quite understand the nuance of the writing style in our source material. Anomalies like neutral-site games and TBD dates for matchups are throwing a wrench in the works.

I'm a lot more hands-on at this point, still not writing any code, but being very prescriptive about how Chaz should handle edge cases. A few updates to string logic here, an escape hatch for undefined dates there, and soon we've got a serviceable JSON array with all 272 regular season games represented!

## Lessons Learned

Leaning on a personified LLM to complete 100% of a coding task was fascinating. In its current iteration (at press time) the bot wasn't quite able to cobble together a fully functional solution. Overall, the job would have been much quicker if I had just hacked together a scraper myself.

But the point was to explore the art of the possible, and to do so with minimal cognitive load on my part. While the overall results were a bit of a mixed bag, I came away with a finished product that meets the stated objective, and Chaz Geppetto has taken a large robotic step toward becoming a real developer. I call that a success!

Looking ahead, I cant help but feel excited and optimistic about the potential of future projects. Much more to follow!

Cheers,
Josh
