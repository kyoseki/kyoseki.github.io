---
title: a retrospective on Become Fumo Scripts
date: 2022-05-30 13:36:53 -0700
categories:
- projects
- roblox
---

## summary

Become Fumo Scripts, created on 7 August 2021, was my first Roblox/Lua project,
and my first project to have a userbase.

Surprisingly, I managed to get a few valuable experiences from its development.

## demonstration

[This video](https://youtu.be/p0AKgwcsFwk) should provide an idea of some of the things this script does.

## the beginning

Become Fumo was, dare I say, the de facto fumo-centric game until it was discontinued this year in May.
I first joined the game around 19 July 2021, a latecomer to some,
and I can't explain why I decided to stick around on this game for as long as I did - I probably shouldn't try either.

Since playing the game was mostly a waste of time to me, I decided to make a project out of it.
After noticing the abundance of exploiters in the game and seeing people removing parts from their character,
I had an idea for what I wanted to make.

On 7 August 2021, I began development on Become Fumo Scripts, an exploit script dedicated to the game (and later its spiritual successor, Scuffed Become Fumo).
It quickly grew to have more impact than I ever expected.

## learning Roblox

Since this was my first Lua/Roblox project, I had two options at my disposal (at least the ones I use most):

1. Research vigorously and start the project once ready
2. The "balls deep" approach - minimal research, do it and fix chaos later

I chose the second option on this occasion.

I went from [YouTube tutorials](https://www.youtube.com/watch?v=dCx_bVm9x88) on exploiting,
to directly consulting Roblox documentation and the sources of other scripts.

My programming experience definitely made this process faster for me -
I've used method 2 on several occassions with some (?) level of success.

Indeed, after a few test scripts, I got started on what became BFS.

## no script kiddies here

I opted against copying random code or using a GUI library for the script because I (probably rightfully) don't trust the Roblox exploit community to make code that fits my standards (and also need to do everything myself due to my heavy programmer ego).

Doing things like a basic GUI framework and a configuration/changelog system from scratch is also quite interesting.

## the charming jank of Lua

Lua is not a very good language.

I understand why it's used in Roblox, though, and I thoroughly appreciate their efforts in [Luau](https://github.com/Roblox/luau).
It's also one of the only (and probably one of the best) options as an embeddable language, intended exclusively for use within other projects.

Please don't use it standalone though.

Anyhow, I was stuck with it for this project (and others), so I had to get used to its janks - or what is different from other languages.

Keep in mind this stuff is mostly just my perspective (i.e. it could be wrong (to you) (or objectively) (I don't *really* know what I'm talking about)).

### insecurity

Lua and JavaScript are somewhat similar in that they don't really protect you from things you (probably) shouldn't do.
For example, it's pretty easy to lose track of what should be passed where as what type, and this leads to errors and frustration.

It's certainly possible to use a language like these (particularly, without static typing) and be successful with it,
it's just more difficult for me to maintain sanity while doing that.

### metatables

[Metatables](https://www.lua.org/manual/5.1/manual.html#2.8) enable a lot of custom functionality in Lua,
including custom adding, subtracting, and even indexing and setting operations.

They're one of the most cool things about Lua itself, especially in how flexible they are.

They're also (just a little bit) evil.

### classes

Lua doesn't have a notion of classes or OOP, something which is confusing and annoying to an OOP programmer like me,
and possibly a blessing to those who dislike it.

Lua "classes" are enabled only by metatables, and the [idiomatic way of doing classes](https://ozzypig.com/2017/04/19/object-oriented-programming-in-lua-part-2-metatables)
and especially inheritance is painful and difficult to remember.

It's probably one of my least favorite things about Lua.

### others

Other things like threads (they don't really exist), yielding, `wait()` (at least the way it works in Roblox),
and the lack of great IDE support extend my like-hate relationship with Lua.

In other words, it's complicated.

## maintaining code quality

One of the biggest limitations of Roblox exploit scripts is that creating a good system of separating source files is difficult.

Probably the best option to take here is to load several files through HTTP, but this takes more time and makes development more tedious.
I adopted it months after development began, hence the `gui.lua` and `becomefumo.lua` split.

As a result of this limitation, BFS is just over 3000 lines long, factoring in the split.
Without the split, it grows closer to 3800 lines.

This makes it necessary to separate code effectively within one monolithic file to manage the chaotic global scope and keep things as separated as possible.

The internet solution to this is to enclose parts of the file with `do` and `end`, which is the reason for this comment at the beginning of the source to BFS:

```lua
--[[
    do - end blocks can be closed in most ides for organization
    variables beginning with c are constant and should not change
]]
```

Surprisingly, even in a Roblox exploit script thousands of lines long, I managed to maintain some semblance of maintainability.

## community ideas

I'm not so great at coming up with original ideas (maybe you can tell), rather I choose to extend others' ideas and make them (somewhat) my own.

To this end, most of the ideas in BFS (with the notable exception of the minimap) are the ideas of others.
I thank these people in the credits of the script, and I'll list them here too just because:

- AyaShameimaruCamera: Replace Humanoid (basic part deletion), inspiration for the script itself
- gandalf872 & LordOfCatgirls - Removing welds (effectively part deletion)
- xowada: Controlling accessories

Taking the ideas of others and polishing them sometimes feels like stealing. Hopefully it's not too bad?

## spread

I initially shared BFS in a Discord server related to Become Fumo.
After the update which included the control of accessories, interest in it peaked (certainly due to the fact that it's highly attention-grabbing).

As a result, this is the first programming project I've done which has/had an actual userbase - tens of them, for whatever that's worth.

## out of control

Trust became an issue when the script got shared to some people who I didn't intend to have it.
I don't *exactly* seek to have authoritarian control over who uses what I make,
but if you've played Become Fumo it goes without saying that some *strange* things happen there - I won't get into that.

This uncontrolled spread caused the creation of a (rather crude) whitelist - one which I think helped control the spread of things,
and also to maintain that sweet, highly coveted exclusivity.

Today, that whitelist has not changed for months, and I've mostly moved on from Become Fumo itself, which is why I'm now comfortable with finally releasing the source.

(not like most people will ever use or read it)

## a unique adventure

Creating BFS brought me closer to a community I probably wouldn't have otherwise stuck around.
It also led into a few other projects, which I will probably go over later.

Overall, I think it was a net positive... maybe.
It definitely carries some memories I'm quite fond of.

Its development is now quite slow, and most of it probably won't ever be updated,
which is why I call this a "retrospective."
It's not officially discontinued, but it basically is until I get further requests
(for bug fixes or small additions).

## valuable experiences

- Maintaining a codebase which could easily spiral into nonsense (3000+ lines)
- Having a real userbase and catering to it for the first time
- Quickly grasping and learning Roblox/Lua
- Growing close to a(nother) community

### some specifics

- Fumbling around with 3D math (CFrames, etc.)
- Creating a minimap and everything that entails

## source code

For those of you who want it, [here](https://gist.github.com/kyoseki/1b29473215daa1e58fc2936905adc53b) is the source code to version 1.7.2.
I might not ever update this public release, but it's not like intend on updating this script frequently going forward anyway.

