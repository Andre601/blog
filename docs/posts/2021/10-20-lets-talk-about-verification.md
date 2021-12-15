---
title: "Let's talk about your verification system Discord..."
description: "A long discussion about why Discord's verification system is flawed."

tags:
  - discord
  - discord-bots
  - bot-verification
  - verification
---

[^1]: https://github.com/discord/discord-api-docs/discussions/3971
[^2]: https://github.com/discord/discord-api-docs/discussions/3731
[^3]: https://forms.gle/iLwefnoEMPsnkNVW9

!!! info
    This blog post has been made after my original discussion[^1] has been locked with a weak explanation that questions may be answered in their upcoming Q&A.  
    I made this blog post, so that people can give their feedback in form of a comment below through Disqus.

## Before I start...
From my last discussion[^2] I learned a few things, and want to make a few things clear here.  
I do not tolerate any comments with targeted hate towards individuals or groups such as Discord Staff Members or Discord itself. I can understand you being upset sometimes but it doesn't give you the freedom to insult or attack others.  
I will report any comment that can be considered insulting towards GitHub for breaking general rules such as Code of Conduct. I want the chat to be civilized and welcoming and not just a place to "let off steam", as good as it may be at first.

Thank you.

## About
Bots that are nearing 100 servers need to get verified by Discord to be allowed to join past 100 servers, but also to gain or keep access to specific, whitelisted intents such as Guild Members and Guild presences (And in future also Messages).

While the whole intent thing is another can of worms I would like to tackle, I do not want to do this here and now.

Instead would I like to talk about Discord's bot verification and how fundamentally broken it is to begin with.  
I will use some data I collected through a survey[^3] I made. While the amount of responses I got is somewhat low (39 participants as of writing this), I still think it is valuable data to work with, mainly because there aren't really any official statistics from Discord themselves to work with.

My post will mainly cover the "Inorganic Growth" issues that a lot of developers are encountering, and I will give my personal thoughts on this matter as well. Enjoy.

## The general issues with intents
Discord's verification system has a few flaws and issues that I can't get behind. One of them being the whitelisted intents.  
It makes sense that you want to put sensitive intents behind a whitelist to not willingly give sensitive data to bots that could abuse it.

The issue is that small bots still can access priviledged intents and data without the whitelisting. While this makes sense for bots that are only on a hand full of servers and are used for things like moderation is it not really covering the data from being exploited.  
While some of you may think that 100 servers isn't that much should you always remember that a server may have hundreds if not even thousands of individual members. This could end up in the bot having access to thousands of individual members without needing whitelisting for the intent to begin with.

I'm not the biggest fan of the priviledged intents, since they caused my bot to lose a few very valuable features in the process, but if you really want to keep this should the intent requirement perhaps be lowered to like 50 servers as no person in the world has a private bot on over 100 servers. At such a point would it be a public bot already.

The next problem is Discord's reason of "privacy". I remember Discord mentioning that the intents were restricted to prevent spam bots or data farms (Sites that collect and display user information without consent) from getting such information that easy. While this may be a good point, the fact that this only applies to bots makes it essentially pointless.  
Sites which collect data without consent of the users often don't use bots, but instead automated user accounts to do so, and as a result can collect the info without any restrictions because the Discord client does have the required intents to work properly.

In addition, "small" bots can still do damage with those intents. How else do you explain the existence of all those "Free nitro" and "Free server boosts" bots?

Finally, a bot is not infallible and can be hijacked at any moment. Yes, it may be unlikely, but it is not impossible, and if the bot is on several thousands of servers AND also has access to the intents could nobody predict what exploits could be done with the data received.  
After all are bot lists and other, larger servers facing almost weekly if not even daily DM spam from bots and automated users.

## Lots of flagging in verification
![Was your bot flagged for Inorganic growth](https://user-images.githubusercontent.com/11576465/137969660-bf97a4d3-caf9-491e-b021-74d4b27485dc.png)

The above graph shows the very first question of my survey, which was whether the dev's bot has been flagged for "Inorganic Growth".  
While the larger part (`56.4%`) of people answered with a "No", we should not forget that this was indeed a simple "Yes"/"No" question, so the remaining `43.6%` answered with a clear "Yes", which even for such a small amount of participants is quite a large number (17 people out of 39).

But why is that? Well, there seems to be one common cause that I noticed and that is bot lists.

## Discord and Bot lists
There seems to be a trend that bots, which are part of (larger) bot lists seem to get flagged more frequently. This kind of makes sense because a bot list increases a bot's rate of being invited to servers.  
One participant of the survey even linked a reddit post, in which they mentioned how their bot started to join dozens of servers a day after it was approved and added to a bot list.

And this seems to be a big issue for Discord. For some reason do they not like it, when people add bots to bot lists and their system will flag the bot for "Inorganic Growth". While this is logical, since it's most likely an automated system that should flag bots having a sudden boost in invites per day, there are still people responsible for handling this flagging... And they are doing a horrible job at it.

## Copy-paste responses and no help

In my survey, I also asked people whether they received a particular message when their appeal was rejected.

![If you appealed and it was denied, was the message you received the same as shown in the description below_](https://user-images.githubusercontent.com/11576465/137969930-6f8742a8-cd94-483a-bc3f-0755bb2da534.png)

Here is some important context regarding this particular question and graph.  
The above graph only depicts responses from devs which...

- Got their bot flagged for "Inorganic Growth"
- Made an appeal towards Discord
- Got their appeal denied

This means that participants who did not get their bot flagged, did not appeal or got their appeal accepted are not included in this graph, since they're not relevant for that particular question.

When we look at it can we see that `91.7%` of participants responded with a "Yes". To put this in perspective: Only 1 single user out of 12 responded with "No"

But what was the message you may now ask? Well, it was this one here:  
> Unfortunately, our original findings have not changed. Your bot's growth pattern and server distribution remain concerning, though we cannot provide exact details on what prompted our concern. We will not be verifying this bot.

This means that Discord, instead of giving any clear explanation as to what made the system flag their bot to begin with and why they won't accept the appeal, just gives a cookie-cutter response to justify this.

Discord, why do you not want to give clear info? Do you really fear we may exploit that? People, especially developers are not the cliche hackers you may think we are.  
We want to improve and feedback to improve is a core part of this. If there is an issue with the bot, then we want to fix it.

Giving some clear info as to what caused the concerns and flagging would allow devs to improve the bot by e.g. implementing an anti-bot-farm system.  
You force the devs to basically guess what the issue is and by that point, it seems like you blame bot lists for doing what they do which is promote and share Discord bots towards others.

You at one point allow us to make and share bots, but on the other side don't allow us to share them with others through common ways including bot lists? Pick a side Discord.

## How can this be fixed?
This is a big question: "How to fix this mess?" and... well... it can be difficult to answer.  
I do have one idea tho:

**Abolish the "Inorganic Growth" check**

This check so far did more harm than good. Many potentially good bots lost their right of showing what they can offer because an automated, faulty system thinks their growth was not legit and caused by the dev and because the staff behind that faulty system doesn't seem to care to even make some basic research and check if the bot is actually doing bad stuff.  
You shamelessly shift the blame to the dev, telling them that they are the ones at fault here because they did what anyone would do to promote a bot: Adding it to bot lists.

YOU constantly promote devs and tell everyone how awesome the community is in building new things, but at the same time do you constantly put stones in our way and prevent bots from reaching potential.

What if one of the denied bots could help servers with preventing phishing attacks?  
What if a bot could help people with mental or physical issues to easier connect to others in a server?  
We never know because you play doorman and keep them out of your place. Your motto is "Imagine a place!", but how should developers imagine anything if the way they can/should promote a bot is restricted by your rules?

You want US to share our bots with the world, but when we do it through methods you don't own is it suddenly "illegitimate" and wrong.  
How are we supposed to share our bots? The "Word by mouth" aproach may work for some, but not all, bots, and a bot list is one of the most common ways to do so.  
It existed for years now and never was an issue, but now with your "Inorganic Growth" detection and what seems like to be a zero-tolerance rule, we are unable to share what we put our time and effort in.

You - once again - destroy the community that started to make you big. Users aren't the only thing on your platforms. It's the bots that can and will bring life and changes to a server.  
Without bots we would not have a way to ban raiders (or to prevent raids to begin with because slowmode isn't the best solution here), detect and eliminate scam and phishing attempts, maintain channels, etc.  
Bots enhance the server and by blocking their growth through a faulty system — which you trust more than the individual people that spend hours on making the bot - you essentially dilute the bot place. Larger bots get more and more exposure and smaller ones stay low because daddy Discord says "No".

Please start to change. Update your system and also accept that adding a bot to a bot list at its start is a common practice and shouldn't be treated as "illegitimate". You make devs and bot lists look like criminals, because of your horrible growth detection.

If you care about privacy and security, actually do actions against bad actors in the community.

- Add a link detection that prevents sending of phishing links. If browsers can have such a detection, so Discord can have to.
- Rework your permission system to have easier ways to implement things like muting-systems, or even better, ADD a mute-system to mute a user server-wide, no matter their roles.
- Improve Audit-logs to include more info from what bots do, like deleting messages of others. You so far give very few info that can actually be useful for mods on a server to see what is happening.

In general, start to actually fix stuff that really matters and don't punish bot devs for being human beings.

Sincerely,
Andre_601

## Special thanks
A special thank you goes tho these groups and people:

- [Discord Bots](https://discord.bots.gg) for bringing the survey to the attention of bot developers.
- meew0 for proof-reading and some additional ideas.

--8<-- "footnotes.md"
