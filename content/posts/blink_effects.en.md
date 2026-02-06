+++
date = '2026-02-06T17:29:27-03:00'
draft = true
title = 'Extending Rich Text'
cover = { image = "images/data/blink.png", alt = "Configuration in Godot", caption = "How to configure the RichTextEffect" }
tags = ["Godot", "Devlog", "Juego", "MPVP"]
+++

### The idea

I've been working on a game that I want to try to submit to MPVP at adva 2026, and part of the look and feel is having it be an old terminal. One thing that really stands out in terminals are the blinking symbols waiting for user input. I know the new version of Godot has pulse, but I wanted to try building a function that does the blink specifically, and in the process learn how to do something similar.

### The code

```
extends RichTextEffect
class_name BlinkEffect

var bbcode = "blink"

func _process_custom_fx(char_fx_transform: CharFXTransform) -> bool:
    var time = char_fx_transform.elapsed_time
    var visible = fmod(time, 1.0) < 0.5
    char_fx_transform.visible = visible
    return true
```

It's as simple as that. By just extending RichTextEffect and overriding the _process_custom_fx function, we can create a new tag to use inside RichText. Maybe it's very simple and far from being a complete feature, but I wanted to share it.

In the code we see how we first mark the tag name, "blink" in my case, then with the elapsed_time property we can know how much time has passed since the text was created. With this time we do a simple modulo operation to get the remainder, which gives us a boolean to turn our functionality on or off.

I owe you the example of what it looks like, but I'm still getting used to Hugo and I don't want to spend a couple of hours fighting with a gif and a static resource that for some reason isn't displaying.
