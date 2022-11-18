---
template: giscus.html

title: How to use Mastodon
description: "A (hopefully) useful guide on how you can use and interact with Mastodon."

date: '18.11.2022'

tags:
  - mastodon
  - socialmedia
  - twitter
  - federation
---

Elon Musk has bought Twitter for an incredible amount of money and has since started to destroy it left, right and center. Employees got fired or resigned, verified accounts lost their iconic blue checkmark and received a grey/transparent "official" badge while the blue checkmark is now something you can buy for $8, and other things I sure can't think of right now.

But all this drama also surfaces some new changes.  
Mastodon[^1] gained a lot of popularity due to the recent events and is currently having around 1.9 million active users on over 6,000 individual servers. People start to move from Twitter to Mastodon as they see the former dying in the forseeable future or at least becoming a less welcoming place for individuals.

Since so many people switch to Mastodon are there obviously some that have a hard time understanding the inner workings of this platform (And federation in general), so with this post will I try my best to explain how to get started on Mastodon.

## The Basics first

First, let us clear up what Mastodon actually is. Mastodon is a decentralized (aka federated) Micro-blogging platform.  
"Federation? What is that?" will you probably ask. In the most layman terms does federation mean, that a service, site, ... isn't controlled by a single company, group or individual. Instead are there multiple servers (so called instances) that communicate with each other, building a network. This has the benefit that this service or site isn't under the control of one individual and can't be shut down so easily. If one instance is blocked/shut down, several others continue to exist.  
Or to put it even more simply: Federation puts control into the hand of the people and not just a single person.

Mastodon is using this concept. It allows everyone to create their own instance with its own settings, themes, rules, topics, etc. to then communicate with other instances in the so-called Fediverse (Federated Universe).

## How to use

I'll now go about the basics of Mastodon, explaining in easy steps how you can use it properly. Keep in mind that those are things I learned myself, so there may be better options for this in the end.

### Registration

Given the fact that there are multiple instances, you may think you have to make an account for each instance to do things like [following an account](#following-an-account), [boosting](#boosting-a-post) or [adding a post to your favourites](#adding-posts-to-favourites), but that is not the case.

On Mastodon do you only require **a single account** for the entire Fediverse. With that said is it sill important, *where* you want to register your account. Each instance has its own rules and also its own set of features. Some may support markdown, others may not. Some may allow all kinds of topics, others are only about certain ones. It all depends on your preferences and what you really want.  
A good site you may want to check is instances.social[^2] which helps you finding the best matching instance based on your preferences. At [the end of this post](#servers) can you also find a list of my personal recommendations.

Once you have selected the instance you want can you create your account. Depending on the instance will your account be ready right after you verified your e-mail, or may require approval of the staff of the instance. It's recommended to check the instance's `/about` page to see if they mention anything particular to look for.

The moment your account is ready can you start posting. Tho you may first want to edit your profile (Avatar, Banner, Bio, Links) and preferences before actually doing that.

### Following an account

Just like on Twitter can you follow individual accounts on Mastodon. Tho, due to how the federation works can it be a bit more difficult to do so.  
For accounts that are on the same instance is it relative easy: Go to their account page and press the "Follow" button.

Accounts on other instances tho are a little bit more tricky, but not that much. First, find out on what instance they have their account. This can for once be checked through their tag. The full tag of a user is `@username@domain.tld` where `domain.tld` is the domain of the instance this account was made on.  
If, for example, you want to follow the `Mastodon` account on `mastodon.social` would the full tag be `@Mastodon@mastodon.social`. To now follow the user, copy the tag and append it to the URL of the instance you use. If the instance would be `example.com`, would the URL be `example.com/@Mastodon@mastodon.social`. This will now show the profile through your instance, allowing you to easily follow it.

!!! info "Note"
    A user can set that follows need to be accepted by them first, before you can see their public posts in your feed.

It's important to note that you can only see public posts from people you follow in your personal timeline. Mastodon doesn't provide nor use analytics to "recommend" posts to you. You have to find the stuff yourself.

### Reply to a post

Replying is relatively easy. Posts made from accounts on the same instance can be replied to by just pressing the button, writing your reply and sending it.  
For posts on other instances is it a little bit more complicated...

You first need to obtain the URL to the post (Example: `example.com/@user/123456789`). Next will you need to paste it into the search bar of your instance and press enter. If everything works well should it be displayed as a result that you can click on.  
You can now reply to it just how you can do it to posts from your instance.

### Boosting a post

"Boosting" is Mastodon's term for "Re-tweeting", meaning that you re-post the message from someone (or yourself) into your own timeline of posts.

Boosting follows a similar principle as [replying to a post](#replying-to-a-post) in a sense that you can just press the boost icon for posts from the same instance, but need to find the post through search for those from other instances.

What is important to note is, that you can't quote a boosted message. You can only boost it as-is without modifications. This was an intentional decition made by the devs of Mastodon as quoted re-tweets usually end up in a lot of drama or other bad behaviours they didn't want on Mastodon.

### Adding posts to favourites

"Favouriting" a post is the same as "Liking" a tweet on Twitter.

Favouriting a post follows a similar principle as [replying to a post](#replying-to-a-post) in a sense that you can just press the boost icon for posts from the same instance, but need to find the post through search for those from other instances.

## Recommendations

Here are a few personal recommendations for getting you started with Mastodon.

### Servers

!!! note "Note"
    Descriptions are taken from the servers themself.

- [`tech.lgbt`](https://tech.lgbt){ target="_blank" }  
  Manual approval? Yes
  
  This Mastodon instance is for tech workers, academics, students, furries, and others interested in tech who are LGBTQIA+ or Allies. All are welcome to join us!
- [`craftodon.social`](https://craftodon.social){ target="_blank" }  
  Manual approval? Yes
  
  English speaking non-official Minecraft instance. For everyone who plays Minecraft, this instance is a mast!
- [`blobfox.coffee`](https://blobfox.coffe){ target="_blank" }  
  Manual approval? Yes
  
  A cozy instance for people that like blobfoxes and/or coffee.
- [`mastodon.social`](https://mastodon.social){ target="_blank" }  
  Manual approval? No
  
  **NOTE:** Registration is currently disabled as of writing this!  
  The original server operated by the Mastodon gGmbH non-profit

### Tools

- [`instances.social`](https://instances.social){ target="_blank" }  
  A site that helps you finding the instance most fitting for your interests and needs.
- [`fedifinder.glitch.me`](https://fedifinder.glitch.me){ target="_blank" }  
  This site helps you finding mastodon accounts of people you follow on Twitter (or that follow you there). Requires authentication with Twitter account.
- [`crossposter.masto.donte.com.br`](https://crossposter.masto.donte.com.br/){ target="_blank" }  
  A tool that allows to post, re-post/re-tweet from Mastodon to Twitter and/or vice-versa. Requires authentication with both Twitter and Mastodon account.

## Special thanks

- The [Mastodon gGmbH](https://joinmastodon.org){ target="_blank" } for making Mastodon.
- The [glitch-soc](https://github.com/glitch-soc) devs for making their fork of Mastodon with Markdown support.
- [Ember](https://blobfox.coffee/@Ember) for making blobfox.coffee, which I use.

--8<-- "footnotes.md"
