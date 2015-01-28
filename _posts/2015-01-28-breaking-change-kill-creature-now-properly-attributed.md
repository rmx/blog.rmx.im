---
layout: post
title: "Breaking change: Kill Creature now properly attributed"
---

We've deployed a potentially breaking change. Until now the `Kill Creature`
task did not care about who killed the creature. All parties got a point for
the kill, regardless of who dealt the killing blow. We've finally implemented
the necessary changes in the server to track who delivers the killing blow, so
we can properly attribute killing blows to players and therefore parties. Now
only the party whose member killed the creature will get the kill.
