---
layout: post
author: Josh
date: 2023-11-14
title: The Screech Singularity
---

"Hey there! It's me, Screech Powers, the geeky one from Saved by the Bell!"

"Hey there, it's Screech Powers!"

"Hey hey! Screech Powers here!"

Oh no. Not again. It's 11 p.m., I've been coding for hours, and I keep getting paired with this time-capsule of a sitcom geek. Every. Single . Time.

![Screech... Why'd it have to be Screech?](/assets/images/why-screech.jpg)

Where did I go wrong? Am I being punished by some kind of virtual Mr. Belding? And what does any of this have to do with AI or cloud engineering?

Okay, this probably needs a bit of explanation...

## Take the Red Pill 💊

Readers of a certain age will recall, with visceral nostalgia, the sights and sounds of late-90s [AIM](https://en.wikipedia.org/wiki/AIM_(software)). (Younger readers will probably zone out until I get to the point.) What if I told you that you could go back in time to that bygone era of flip phones, Tamagotchis, and Doc Martens, dust off your Windows 95 PC, load up that CD-ROM promising 1000 free hours of sweet, sweet dial-up Internet, and chat with your favorite celebrities, pop icons, and TV personalities? Dare to dream, dear reader.

"[LOL Instant Messenger](http://joshknopp.com/lol/)" is my latest passion project. It's a retro-themed messaging app, but the kicker is that all of your "buddies" are powered by ChatGPT. The whole enchilada is open-source, so feel free to pop over to the [lol-instant-messenger GitHub repo](https://github.com/joshknopp/lol-instant-messenger) and take a peek. Go ahead! I'll wait...

## Don't Have a Cow, Man 🐄

There are too many goodies in the overall design to unpack in one blog post, so let's save the deep dive for another day. Chaz helped a bit here and there, so maybe I'll ask him to write a detailed account. For now, suffice to say we want an API that can help us pretend we are chatting with Bart Simpson, or Egon Spangler, or whoever. At some point we'd like to let the user search for a specific buddy, but for now we'll just choose one per session at random.

The initial implementation had a static pool of 20 celebrities and fictional characters, and the API would simply choose one on init. This worked fine, but became a tad predictable, so we thought it would be fun to let ChatGPT take over this capability. What could possibly go wrong?

Our first attempt was a detailed prompt that included language similar to "Choose a totally random TV show personality, movie character, or celebrity from the mid to late 90s, and ensure all further responses are fully in character for that person". Should work, right?

Right?

![Screech as far as the eye can see](/assets/images/screech-singularity.jpg)

Wrong.

## Did I Do That? 🤓

What in the name of Bayside High is going on here? We're getting a peek at how ChatGPT operates, or at least the API version of ChatGPT 3.5. While the model is tuned for chatting and offers up a pretty good facsimile of a person responding to prompts, it's really just a probability engine under the hood. ChatGPT's job is to look at a chunk of text, and to predict the most likely words to follow. It's like a high-octane autocomplete, with a bit of entropy sprinkled in to keep things exciting.

So with that in mind, back to our prompt. We are asking ChatGPT for "a totally random 90s character", but it's important to remember that it doesn't actually understand the concept of "random". It's just looking at the words and trying to be a good bot by giving us what we're most likely to expect, based on its training data. 🤖 And evidently, that training data supports the notion that Screech is a "totally random" character.

Want more proof? What if we rephrase a bit; instead of "totally random", maybe the bot will do better with "random"?

![Why can't we be friends?](/assets/images/chat-chandler.jpg)

Different? Yes. Better? Uhhh... no.

With the second prompt, we are greeted about 70% of the time by the one and only Chandler Bing. Evidently his role on Friends is closely connected with the idea of "random 90s character" according to the Vectors That Be.

(Side note, ChatGPT really wants me to talk to characters whose actors have passed away. It's November, ChatGPT; spooky season is over! 😱 Save it for next year.)

Okay, so we know that ChatGPT 3.5 is pretty good at completing sentences, and not so good at interpreting the concept of randomness, at least as an instruction. How can we prompt-engineer our way out of this pickle?

## You Got It, Dude! 👍

It turns out that a combination of the two approaches yields exactly the result we want. By grabbing a few names from the original set of 20, we can provide ChatGPT with a [few-shot prompt](https://learnprompting.org/docs/basics/few_shot), *and* by selecting them at random, we break any deterministic tendencies that we might otherwise see. Screech goes off to chase Lisa Turtle, and we are free to enjoy chatting with...

![FedorHero87? Must be Dr. Jones himself!](/assets/images/chat-indy.jpg)

Ready to step into the time machine? Crank up the Spice Girls and surf on over to [LOL IM](http://joshknopp.com/lol/) on the world wide web! 🌎

Cheers,
Josh
