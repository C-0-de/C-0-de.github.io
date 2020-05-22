---
layout: post
title:  "Unity Ticks And Stuff"
comments: true
tags:
    - Unity
    - coroutine
    - time
---
## Time is an illusion
    Game Development on Unity often gives you time-based problems. By this I mean you have an update which happens every frame. But what if you wanted something to happen later?

You end up with weird code that is checking over and over - like children on a long car journey asking “are we there yet?!” Or impatiently waiting by the door for an Amazon delivery.
![ Any second now... ](https://media3.giphy.com/media/axdZ8oK30cTCM/giphy.gif)
A code example of this:

float timer = 0;
float cooldown=30;
private void Update() {
    timer-=Time.deltaTime;
    if (timer<=0){
    DoThing();
    timer = cooldown;
    }
}

or worse...

float start =Time.time();
while (Time.time()-start>0){}
DoThing();


This is fine. It works. But it is also ugly and takes many lines to express the concept of “do this thing later”.

We can instead be more productive with our time and write cleaner-looking code. Why don’t we set an alarm and come back later?

![ got places to be! ](https://i.giphy.com/media/SU6pRekIDqhna/giphy.webp)
 
## Two things at once

In Unity, most things happen in one thread. This is fine, but it does make the polling method - the while method particularly - problematic.

Unity offers useful tools for this in the form of a coroutine. The basics of a coroutine is built on IEnumerable - which is a fancy way of saying has iterations.

You could have one to count up from zero, and keep going for as long as you ask it what the next number is. That’s because an IEnumerable has some state to know where it is, and how to get to the next state.

What’s this got to do with coroutines? Well, we use this to break up code. Once it’s broken up, we can swap back and forth between all the different jobs we have to do. Like spinning plates, we go round each in turn keeping them stable.

![ oh Salem ](https://i.giphy.com/media/EndmKkbSJeFwY/giphy.webp)

## I yield my time
So after writing code which can be split up, the next step is to tell the programme where to split it. The computer can’t guess this for you as it doesn’t know when it would be safe to do so.
This is where the yield keyword comes in. This is the magic incantation to say “I’m done for now.” In some cases, you may wish to return to this bit of code. In this situation, the yield keyword can also be used to signify “here’s what I’ve got for you so far.”

Unity Time
Until now, this blog has been very abstract. So let’s bring it all together in an example.

Unity coroutines have functions available in them, like WaitForSeconds(s). This lets your function set an alarm to continue execution later.

![ alarm clock ](https://i.giphy.com/media/gBW8Qgfaa2ije/giphy.webp)
Here’s an example of how to set this type of alarm...
void Awake()
{
  StartCoroutine(DelayedGratification());
}

IEnumerator DelayedGratification ()
{
    Debug.Log("The antici-");
     yield return new WaitForSeconds(10);
    Debug.Log("pation");
}