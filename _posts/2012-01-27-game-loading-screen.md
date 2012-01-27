---
layout: post
title: "Game loading screen"
---

When entering the game we used to display the 3D canvas right away and loaded
the models in the background. This was confusing in multiple ways:

 - The player was left staring at a black screen for the first few seconds.
 - No visual feedback how long the loading would take.

To fix that we've created a loading screen. Now we display a progress bar
while the models are being downloaded, and only when that is done we show the
3D canvas. Here is a preview of the progress bar:

<span class="center">
  <span class="shadow">
![img](/assets/post/2012-01-27-game-loading-screen/game-loading-screen.png)
  </span>
</span>
