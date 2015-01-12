---
layout: post
title: "Encounter leaderboards"
author: "Tomas Carnecky"
---

A while ago I implemented the necessary backend changes to support
leaderboards. Even though it's a nice feature to have – it allows players to
compare their performance and skill with each other – I haven't seen
a widespread adoption of it. The most likely explanation is because nobody is
aware of its existence. And that is what this post is trying to rectify.

The leaderboards are currently hidden, there is no direct link to them. If you
want to view them you have to append `/leaderboard` to the public encounter
page, eg:
[https://rmx.im/e/TOuhroQZWm/leaderboard](https://rmx.im/e/TOuhroQZWm/leaderboard).
They don't look very good yet, and I've already received a complaint from
a user to improve the look. I'm aiming for something similar to the [WoW
challenge mode
leaderboards](http://eu.battle.net/wow/en/challenge/dungeon/skyreach).


### How are leaderboards generated?

Only games in which one of the parties has won will be considered in the
leaderboard. Games where no party has successfully completed all required
objectives will not show up in the leaderboard. The eligible games are sorted
according to the following key:

*highest score -> lowest duration -> earliest creation date*

That is, if two games have the same score, the one which completed the
objectives faster (lower duration) is better.

### Score

Score is a new concept which is used to compute the leaderboard. Each *party*
has a score. The score is updated by the *scoring function* – an *expression*
which is run everytime something in the game changes. The *scoring function*
can decide based on what happened to increase or decrease the score of some
parties.

To edit the *scoring function* go the the main encounter editor page and
select *Scoring function* from the sidebar. If an encounter doens't have a
*scoring function* defined then no leaderboard will be generated.

Here is an example *scoring function*, one which gives all parties a point for
each killed entity:

```coffeescript
if eventType(event) == 'soul' && !isAlive(event.content.entityId)
    parties.forEach (party) ->
        modifyScore party, +1
```

