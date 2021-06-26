---
title: Critique versus Hate
description: When people can't take the critique of someone.
---

--8<-- "back.md"

[^1]: https://github.com/renovatebot/renovate/discussions/10610
[^2]: https://docs.renovatebot.com/install-github-app/
[^3]: https://squidfunk.github.io/mkdocs-material/getting-started/
[^4]: https://stackoverflow.com/questions/63287292/how-to-combine-multiple-javadoc-into-one-using-gradle

# Critique versus Hate

!!! note "Terminology"
    I will use the term "Product" throughout this post.  
    With this term do I mean any kind of tool, app, software or other (non-)physical object a user might use.

Since several years now am I a part of GitHub but also other places all around software.  
And many times do I get attacked for simply providing some form of critique towards something, because it's seen as hate.

This post acts as my way to explain to you why my way of feedback may look aggressive but sure isn't.

## Honesty =/= Hate
Whenever I give an honest opinion about a product (Such as my recent case with Renovatebot[^1]) do people start to see it as a personal attack, which I guarantee it isn't.  
The tone in which I talk about things may be a bit harsh or too honest for your taste, but believe me. When I would truly go aggressive towards you, would you not have a good day anymore.

Trust me when I say that I don't want to hate your product, but instead want to share my experience with it so that you can improve on it.

## Wrong expectations
I noticed more than once that some people have an attitude towards people like me, in which they blindly assume that I already know everything there is to know, to use their product.  
This can be anything: From reading and understanding the docs, to executing certain (advanced) commands in the terminal or similar.

The truth is, that this is a faulty expectation.  
While it is normal to assume, that some products may require a bit more advanced levels of knowledge should you also always be ready for people that may need more help in understanding things.

Take my previously mentioned case of Renovatebot. I never really used it before and was more used to Dependabot, which not only has a different, more simplified configuration file, but also doesn't offer any feature that Renovate does.  
On top of that does the docs, while detailed, not give a lot of cross-links to go to pages of interest in f.e. the "Getting Started" Guide[^2].

Now take for comparison Material for MkDocs' Starting Guide[^3].  
On these docs do we have a lot of detailed explanations with links to various other pages to explain specific key-points in more detail. In addition does it have a more natural progression of difficulty:  
You start out with how to install the theme alongside MkDocs, then get an explanation on how to create your first page, followed by how to publish it. Only after that do they give you more advanced things such as how to customize the theme, but this is logical since it's now expected that you have the knowledge from the previous steps to progress.

Always assuming that people have at least *that* level of knowledge, only to then act annoyed when someone askes more beginner-questions is not a good way to go.

## Take the critique and not hate it
When I complain about things do I mean it in a sincere way.  
I do want to use your product and I do have interest in it, but I don't like it when I get forwarded to a documentation with only the bare-bone explanation done.

You by now should've noticed it, but I have a bone to pick with Renovatebot. The way (one of) the maintainer(s) responded to me was kind of egoistic and in a way that (again) assumes I already know the more complicated parts of the bot.  
"How do I ignore a specific Dependency?" -> "`ignoreDeps`".  
This is one of the most lazy answers to pick. Yes, the docs explain `ignoreDeps` and I can search it up, but it still doesn't explain how the String needs to look like to ignore a specific dependency. Do I only set the package path? Do I set the artifact too?  
The way this answer was presented without any real context makes it much harder for me to understand and like this software.

I do ask a lot of (admitedly) stupid questions, but this is all because of me trying to wrap my head around a topic.  
The way I understand and learn things is wastly different from what you and others may understand, so hating me because I critizise the documentation you have is in no way good. Try to take this critique and improve on it. Ask me what could be done better or link me to the docs if they're open source.  
All I want is to understand a product so that I won't have to ask at later points in my life.

This is also one reason why I hate the "Reputation-requirement" on StackOverflow for even commenting on a question or answer...  
Seriously? How should people understand solutions if they can't even ask relevant questions towards the person giving the answer? This stops progress and is a huge waste because it causes duplicate questions to appear[^4].

## Final words
With all this said do I hope you understand me now and that you won't react aggressive or priviledged when I ask stupid questions or give some harsh feedback.  
Again: All I want is to use your product in the future and for it to improve over time.

Just reacting like I insulted your product AND your family on top of that and do actions like locking conversations (\*stares at Renovatebot Maintainer\*) is really not good and harms your reputation more than I ever could.  
After all is everything I want to have answers to my questions and some assistance. I'm often new to certain things and therefore need more help than others, so don't treat me like your worst enemy but rather like one who wants to improve and learn.

--8<-- "footnotes.md"
