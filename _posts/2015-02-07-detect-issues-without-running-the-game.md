---
layout: post
title: "Detect issues without running the game"
author: "Tomas Carnecky"
---

I've tried to make the data structures which describe an encounter so that
they can never be incomplete. Unfortunately that is not always possible.
I can't statically prove that the definition of the encounter is sound, that
it will run properly and not crash. Until now the authors had no other choice
than run the game and hope for the best.

Not anymore! A few days ago I wrote the necessary code in the editor to detect
certain types of issues and show them in the navbar. Next to the play button
(in the very top right of the browser window) you'll see a button which shows
you how many issues were detected. If you click that button you'll be
redirected to a screen which shows all of them in a list, and from there you
can go and fix them. Only certain types of issues will be detected now, but
we'll add more as we come across them.

There are different types of issues, though the UI doesn't distinguish them.
For example you'll get a warning if one of your spells has no icon. Or if
a spell has no spell effects. These types of issues are non-fatal, the game
ill run fine if you don't fix them. They may lead to a bad user experience (a
missing icon) or simply not make sense from a game mechanic point of view (a
spell without any effects).

Then there are issues which will cause the game to crash, for example if you
have an *ApplyAura* spell effect but don't specify a valid aura to apply
(because you forgot or the aura has been deleted in the meantime). These
issues will cause a runtime error. You should fix those before attempting to
run the game.

As always, the user interface is still work in progress.
