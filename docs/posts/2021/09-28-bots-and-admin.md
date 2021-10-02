---
title: Why you shouldn't give bots Administrator
description: A detailed explanation about why it is dangerous giving Administrator to bots or asking for it.
---

--8<-- "back.md"

[^1]: https://www.spigotmc.org/threads/414289/
[^2]: Nuking refers too the process of "destroying" a server by deleting all channels, changing the server icon and/or name, banning every member possible and/or spamming too.
[^3]: https://www.spigotmc.org/resources/18494/
[^4]: https://docs.discordsrv.com/Installation/
[^5]: https://docs.discordsrv.com/Installation/#give-the-bot-the-discord-permissions-it-needs-to-run
[^6]:
    Here is an example from my own bot which does not allow administrator as a valid permission for itself:  
    ![!image 1](/blog/assets/img/posts/bots-and-admin/image-1.jpg){: loading=lazy }

# Why you shouldn't give Bots or ask for Administrator

!!! info
    This post is originally from SpigotMC[^1] but I decided to make this blog post to also improve some things from the original.

Bots are a wonderful thing on Discord. They can enhance and improve your Discord server and also protect it from harm.  
However, a bot isn't unfailable and security is only as save as the person managing it. Because of that is giving the `Administrator` permission to a bot one of if not even the most dangerous thing you can do. The same goes for asking for this permission in the OAuth2 invite or even relying on it to function.

This Post will list my reasons about why you shouldn't give a bot Admin, or as the bot dev not ask for it in a Bot's invite, and what the common dangers are. Enjoy.

## Admin = All permissions without restrictions

!!! quote "Description of Administrator Permission"
    Members with this permission will have every permission and will also bypass all channel specific permissions or restrictions (for example, these members would get access to all private channels). **This is a dangerous permission to grant.**

As mentioned in the description of the Administrator permission does it grant access to all permissions on a server and also bypasses any channel-specific perms and/or restrictions, allowing full read and write access to all channels on the server.  
Discord even mentions that this is in fact a dangerous permission to grant, yet bots get it on a daily basis for multiple reasons (which I explain later on in this post).

With this permission could the bot do pretty much anything without anyone else being able to stop it, except for the owner and administrators which have a higher role.  
The only thing the bot can't do is delete the server as this is only doable by the Server owner themself.

## Bots are NOT safe!
A Discord bot will NEVER be as safe as the dev claims. No matter how many times they mention how secure their bot is, will that not protect them from the biggest cause of errors: Being human.  
The bot's security is only as good as the people behind it. A unprotected eval-command, a leaked token or a hijacked account of the bot dev is enough for a malicious person to gain access to the bot and cause chaos towards the servers.

And let's not forget that a developer may not always be a pure-of-heart person. They can at one point have a hate towards others.

The fact is, that you should treat a Bot like a new user you never saw before and that randomly DMs you. Treat it carefully and don't just blindly trust it straight away.

Or ask yourself this: What is easier for you to do when a bot went rogue?

- Just undoing the mass-bans the bot did.
- Undoing mass-bans, recreating deletec channels, changing back the server's name and icon, recreating all the roles you had, ...

Administrator causes more harm than good in the long run. It may save you time, but at the cost of possibly getting your server nuked[^2] at the end.

## Why do people give/ask for Administrator?

!!! quote ""
    *If this permission is so dangerous, why do people give it to bots? And why do Bot-developers ask for it?*

Well, this can have different reasons, which I will cover some of here.

### Reason 1) Laziness
By far the most common reason for this. Giving the `Administrator` permission is easy and saves time because you don't have to setup channel-specific permissions.

In todays day and age do we try to save time wherever possible and setting up channel permissions is also no exception from this goal.  
To be fair is this also to partially blame on Discord's permission systems where a **granting** permission overrides **denying** ones, EVEN if the granting one is **below** the denying one.

People want to spend as less time as possible in setting up permissions which is why they often just give whatever the bot askes for without questioning it.

### Reason 2) Bad role models
Another cause of this are other bots, sites, services, etc. which are bad role models as they essentially tell you to do this.

One bad role model is the popular Spigot plugin DiscordSRV[^3].  
In their Installation Guide[^4] do they mention the following thing in the step "Give the bot the discord permissions it needs to run"[^5]:

!!! quote ""
    Go to the `Roles` tab and create a new role. We've named ours `Bot`. **Add the `Administrator` permission (or permissions listed below) to the new role.**

This has one major flaw, which is the lazyness of people.  
As mentioned before are people lazy and often look for the way of the least effort to continue. And because of this will they often not bother scrolling to the permissions section and instead just give the `Administrator` one.  
Another more unrelated thing is, that they suggest you give the `Mention @everyone, @here and All Roles` permission which is simply stupid.

----

Another bad role model are large bots.  
Bots such as Dyno, Rythm or Mee6 often ask for Administrator (Sometimes even with any other permission in existance) in their OAuth2 invite, which is more than questionable.

Those bots encourage lazyness because now you don't have to bother with the permissions as a whole.

## What can you do against this?
You may now ask "But what can/should I do against this?" to which I have some answers.

### "Duce Exemplum" (Lead by Example)
If you're a bot developer, stop asking for Administrator in your bot's invite. If people still give it was it their concious decition and you can't be blamed for their lazyness here.  
If you REALLY want to do something good, force people to actually abandon the Administrator perm aproach by denying command-execution and similar while the bot has this particular permission[^6].

You and your bot should be a role model to everyone. If you say you value safety and security, then lead by example and ask for the right permissions and not just Administrator.

### Think before granting
You should always think first, if the bot actually needs those permissions.

- Does a Music bot really need `View Audit Logs` permissions?
- Can it work without it?
- What bare minimum permissions can a bot work with? What other perms are only benefits (i.e. custom emotes)?

You should always think about what a bot really needs and not give it everything.

## Final Words
Thank you for reading.

I hope that by now you understand the possible dangers of the Administrator permission and why you should always think twice instead of blindly giving the permission to everyone and everything.  
And if you still don't think the perm is that dangerous, ask yourself this: Why would Discord themself mention that this is a dangerous permission to grant, if it isn't in your eyes? If they say it's dangerous, then it sure is!
