---
layout: post
title: "Games are played for a purpose"
---

During development of an encounter the authors get to play it many times over
and over. These games are different from those played by ordinary users. For
example they should not show up in the leaderboard, not count towards any
public metrics (such as number of times the encounter was played) etc. But
until now we didn't distinguish between ordinary games and those created by
authors to verify whether the game behaves as expected.

This distinction also makes a difference in certain parts of the user
interface. When authors test encounters, they want to have a shortcut to the
editor, so that the *edit -> test -> edit* feedback loop is as quick as
possible. But ordinary users don't need this, and they'd rather have a shortcut
to the leaderboard, encounter details etc.

To remedy this we introduced a new field in the `Game` object: `purpose`. Its
value is one of:

  - **Verification**: One of the authors has created the game to check
    whether it behaves like expected. Such games will not be included in the
    leaderboard and may be eventually garbage collected.

  - **Grading**: Ordinary players create these types of games. The grade of
    these games can be computed, so they are included in the leaderboard.
