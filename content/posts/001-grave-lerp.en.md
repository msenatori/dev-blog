+++
date = '2026-02-03T19:13:57-03:00'
draft = false
title = 'Challenge #01: Grave Lerp'
tags = ["Godot", "Devlog", "Challenge"]
cover = { image = "images/001/banner.png", alt = "Original game sketch", caption = "The original plan on paper" }
+++

The idea is simple: break the ice and complete a full development cycle (idea, code, bugfix, deploy) in a single afternoon.

### Theme & Objective
The player is an object that follows the mouse with a smooth delay (**lerp**) and must dodge circular saws.

We want to learn how to make a quick little game using some `RigidBodies` and a `CharacterBody`. It's the first thing I imagine; surely there are thousands of ways to do it, but I'm trying to solve it **however my instinct tells me at the moment**. Obviously, this post was written after development, but next time maybe I'll post the plan before and the result after to see what happened.

![Gameplay Screenshot](images/001/gameplay.png)

### The Logic
The idea is to move the player and dodge the saws falling from the sky.
Since it's probably going to be too easy to dodge, I plan to make the game get much faster by **scaling the enemy respawn speed**. I guess to make it a bit more entertaining I'll add a timer to see how far you can get.

#### From Paper to Code
The truth is I'm terrible at designing, but well, I imagined something like this, don't roast me.

![Original Sketch](images/001/idea.png)

### The Bug of the Day
I ran into a classic Godot 4 problem: The saws weren't detecting the floor.
It turns out there is a property that needs to be enabled to activate collision reporting.
1. Configure **Contact Monitor** on the RigidBody to detect impact.
2. Set **Max Contact Report** to 1.

### Completed Tasks

- [x] Create main `Node2D` scene and attach a Level Controller to orchestrate everything.
- [x] Add a CanvasLayer to set up all the UI.
- [x] Add logic to **Instantiate/Delete** enemies (no complex Arrays, pure web performance).
- [x] `CharacterBody` with smoothed movement (Lerp).
- [x] Add *Reset Level* button (Instant Game Over).
- [x] Add a TileMap to build the level quickly.

### Notes
- It probably won't have sound, I don't think I'll make it (and I didn't 😅).
- I didn't sit down to figure out how to configure a complex theme; that's pending for next time.

### Play
The game runs natively in the browser.

[👉 Play on Itch.io](https://arcou.itch.io/001-grave-lerp)

---
**Assets:** [Pixel Adventure 1](https://pixelfrog-assets.itch.io/pixel-adventure-1) by Pixel Frog.

**Approximate time:** 2 hours.
**translate by:** Google translator.