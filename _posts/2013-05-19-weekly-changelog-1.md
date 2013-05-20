---
layout: post
title: "Weekly Retrospect (Changelog)"
published:false
---

We recently decided to (try to) post brief write-ups about our ongoing
development on Encounter. Drop us a line on g+/twitter/facebook for comments
and suggestions.

And so, without further ado, in the last two week, we

* released the [Showcase encounter](http://encounter.io/encounters) to
explore the available tile sets and models,
* started tuning spells and roles of new encounters we have been working on
recently, and
* merged our Sparks.js rewrite (in Coffeescript) and relative positions for
particle effects.


A couple of weeks ago we decided to focus our hacking session on tuning and
testing some of the encounters that we created in an effort to provide fresh
and challenging content: Rescue a princess suffering from Stockholm syndrome
without collateral damage, fight a giant prophetic bug or manage an army of
minions to gather treasures. Tuning all the new roles and spells for each
encounter still requires more time but we expect to release them gradually in
the upcoming weeks.

With the new position mechanism for particle effects, we finally support
particle sources that move with units. The particle effect definition
distinguishes two position types: absolute (coordinates or unit) and relative
(unit or labeled vertex):

    "zone": { "SphereCapZone": ["relunit pos_label", 0.5, 0.6, 80] }

The exact specification of the position is deferred to the spell script, where
previously defined position labels (`pos_label`) are resolved to world
objects, e.g.

    particleEffectStart "name", {pos_label: target}, {}

If not otherwise specified, the `self` label will always point to the
currently controlled unit.

<span class="center">
  <span class="shadow">
![img](/assets/post/weekly-changelog/mage_part_effect.png)
  </span>
</span>
