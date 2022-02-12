---
template: giscus.html

title: Alternatives for JDA-Utilities
description: A list of alternatives for JDA-Utilities that also lists pros and cons

tags:
  - jda
  - jda-utilities
  - jda-utils
---

[^1]: https://github.com/JDA-Applications/JDA-Utilities
[^2]: https://github.com/DV8FromTheWorld/JDA
[^3]: https://discord.gg/jda

JDA-Utilities[^1] is a library made for JDA[^2].  
Unfortunately has the library entered a state of not being updated nor maintained anymore. While core-parts still function fine is the library lacking a lot of features that would make it better in the long run.

This page attempts to list all known alternatives for (parts of) JDA-Utilities.  
If you know an alternative that isn't listed here, let me know in the JDA-Discord[^3], so that I can update this page.

!!! warning "Note"
    The list is in **no particular order**.  
    The position of an entry does not evaluate into how good or bad it actually is.

## JDA-Commands
https://github.com/rainestormee/jda-command

A Command Library for JDA.  
Note that this library does NOT have an in-build command handler. You will need to setup your own. Additionally does the library use a Annotation-based system for a command setup.

!!! info "Features"
    - Commands: :fontawesome-solid-check:{ .octicons-true }
    - Slash-Commands: :fontawesome-solid-xmark:{ .octicons-false } (Planned)
    - Event Waiting: :fontawesome-solid-xmark:{ .octicons-false }
    - Pagination (Menus): :fontawesome-solid-xmark:{ .octicons-false }
    - OAuth2 (Extra scopes): :fontawesome-solid-xmark:{ .octicons-false }

## JDA-Chewtils
https://github.com/chew/JDA-Chewtils

Fork of the original JDA-Utilities with added support for Slash-Commands and other beneficial changes.

!!! info "Features"
    - Commands: :fontawesome-solid-check:{ .octicons-true }
    - Slash-Commands: :fontawesome-solid-check:{ .octicons-true }
    - Event Waiting: :fontawesome-solid-check:{ .octicons-true }
    - Pagination (Menus): :fontawesome-solid-check:{ .octicons-true }
    - OAuth2 (Extra scopes): :fontawesome-solid-check:{ .octicons-true }

## BotCommands
https://github.com/freya022/BotCommands

Command library that also offers support for Event waiting and other things

!!! info "Features"
    - Commands: :fontawesome-solid-check:{ .octicons-true }
    - Slash-Commands: :fontawesome-solid-check:{ .octicons-true }
    - Event Waiting: :fontawesome-solid-check:{ .octicons-true }
    - Pagination (Menus): :fontawesome-solid-check:{ .octicons-true }
    - OAuth2 (Extra scopes): :fontawesome-solid-xmark:{ .octicons-false }

--8<-- "footnotes.md"
