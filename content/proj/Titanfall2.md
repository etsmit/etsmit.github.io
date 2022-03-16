---
title: "Titanfall2"
date: 2022-01-30T13:49:16-05:00
draft: false
---





I am a [leaderboard moderator](https://www.speedrun.com/titanfall_2) and speedrunner of Titanfall 2! Speedrunning is a hobby centered around completing a video game as fast as possible, using glitches, skips, and exploits. Each game is incredibly unique in the ways it can be broken apart and progressed through. Titanfall is a little bit of an exception, as there are not very many glitches used throughout the 1.5 hour run. We only go out-of-bounds twice, and only skip two scripted fight sequences. Instead, runners rely on lots of hours of practicing good movement and combat skills to complete levels as fast as possible.


Titanfall 2 is a heavily trigger-gated video game, in that in order to complete each level, we have to physically pass through a collection of trigger areas. A lot of these triggers do not extend out-of-bounds, which means we usually have to go through the entire level in order to get to the end and have the game actually move on to the next level. This is *not* the case for one of the most boring (to speedrun) levels, Into the Abyss 2. In this 6 minute level, a global auto-scrolling series of platforms move through the level on a set speed. There is a ton of really interesting platform movement and dynamic parkour that can happen in this level, and it is actually really fun in a casual playthrough! However, it is somewhat tricky and we opt to skip alot of that in the speedrun. In order to reach the end, we have to wait on these platforms and ride them to a first domed area. After waiting some more time, we get teleported up into the sky to a second domed area, where a scripted fight sequence takes place. Up in this second dome, the end-level trigger is always there, from the beginning of the level. So - if we can figure out a way to get to this trigger without waiting on all the platforms, we can finish the level quickly without having to wait 6 minutes.


{{< figure src="/images/abyss2blender.png"
caption="Abyss 2 imported into Blender" >}}

A special blender tool was created to import Titanfall 2 maps with all the triggers, shown above. We start up in the tower-looking thing in the top left, move down into the lower part of the level and ride the platforms all the way around up into the first dome, which is outlined in green in the center of the picture. From there, the game teleports us to the second dome, outlined in purple and blue in the top center. We do an out-of-bounds trick to get teleported directly to the end-level trigger, which is the small orange box.

There are two possible ways to reach the trigger without waiting for the platform. The first is to route out an out-of-bounds route that hits all the level triggers and starts the teleport sequence. This *has* been done, but the route takes about 15 minutes to complete - far more than the current 6 minutes it takes. The second way is to induce what is known as "glitch state" - an exceedingly rare game state where the player's hitbox does not act correctly, allowing you to "phase" through many walls. [Here is a clip of Bryonato getting glitch state while practicing.](https://clips.twitch.tv/ScarySingleBoarUWot-YFySZXFGMlWTizb5) At the end of the video, you can see how they walk/see through some of the rock faces.

It is theorized that glitch state is caused by the checkpoints not saving correctly, or getting something corrupted. If a consistent way to get glitch state is found, we may be able to route and out-of-bounds path directly to the level trigger. Finding this is difficult, however. Instead of trying to brute force it in-game, we can check out the game's code. Much of the level scripts are written in [Squirrel](https://noskill.gitbook.io/titanfall2/documentation/file-format/nut-and-gnut-squirrel), so we can read when and where the game is calling certain functions:

{{< figure src="/images/savegame.png"
caption="Squirrel script calling the SaveGame_Create function" >}}


But most of the heavy lifting is done by the game engine, which has been compiled into dll files. We can decompile these, but the result is a mess of assembly code and un-documented C code. We can try to reverse-engineer some of these functions with the help of Cheat Engine, but it would be a massive effort to understand how the game saves checkpoints this way.

{{< figure src="/images/clientdll.png"
caption="Decompiled client.dll file, with assembly code on the left and corresponding C function on the right. No variable/function names have been preserved." >}}

I've been super interested in this side-project, and I've had a lot of fun trying to dissect this game and break it apart. It's been very gratifying to learn all the different softwares and coding languages involved, and piece together how the game works at a low level. (Not to mention, community members have raised a staggering $2000 bounty to whoever finds a skip for this level!)
