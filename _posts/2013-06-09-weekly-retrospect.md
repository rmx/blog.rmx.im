---
layout: post
title: "Weekly Retrospect (Changelog)"
---

While testing/playing the new content with 3 players was enormously fun, we
noticed some shortcomings that needed our attention this week:

* target selection was rather painful: picking does not working as well as we
would have hoped and cycling through all targets can be agonizingly slow,
* threat management is still not behaving completely to our liking,
* we noticed a recurring and large consumption of resources when playing
encounters most likely entailed by the particle system.

Besides introducing a "smart" target cycler (cone in front of the player) to
address the picking problem, we introduced a new label to mark world objects
that are not selectable. Additional key bindings should ease the selection of
group members and their targets:

* `ctrl+1-5`: select party member, and
* `q`: assist target.

A quick CPU profiling hinted that the performance problems occur when the
garbage collector is active. As a first countermeasure we started to use the
Three.js `BufferGeometry` in some places and fixing the caching of models when
loading encounters.

Moreover we found some memory leaks in the particle system class. After
addressing the performance is back to an acceptable level.
In order to prevent the garbage collector from stealing too many CPU cycles
we might have to start reusing memory more aggresively in the future.


On the side we started to thinker with new particle modifiers, like vortices

<span class="center">
  <span class="shadow">
![img](/assets/post/weekly-changelog/part_eff_vort.png)
  </span>
</span>

We will introduce more modifiers and zones as we continue to write particle
effects for current and upcoming encounters.
