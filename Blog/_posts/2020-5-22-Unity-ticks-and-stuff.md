 

## Time is an illusion

Game Development on Unity often gives you time based problems. 
by this I mean you have Update which happens every frame. but what if you want something to happen later? 
you end up with weird code that is checking over and over. like it's an impatient toddler sitting by the door for their amazon package. 
 

![ Any second now... ](https://media3.giphy.com/media/axdZ8oK30cTCM/giphy.gif)

a code example of this:
 
    float timer = 0;
    float cooldown=30;
    private void Update() {
        timer-=Time.deltaTime;
        if (timer<=0){
        DoThing();
        timer = cooldown;
        }
    }
or worse 

    float start =Time.time();
    while (Time.time()-start>0){}
    DoThing();

this is fine, it works. Its ugly and takes many lines to express the concept of "do this thing later. but we can be more productive with our time. why don't we set an alarm and come back later.

![ got places to be! ](https://i.giphy.com/media/SU6pRekIDqhna/giphy.webp)
 
## Two things at once
in Unity most things happen in one thread. this is fine but it does make the polling method. the while method particularly, problematic. 

Unity offers useful tools for this, in the form of a coroutine. the basics of a coroutine, its built on IEnumerable. which is a fancy way of saying has iterations. 
you could have one to count up from zero, and keep going for as long as you ask it what the next number is.
thats because an IEnumerable has some state to know where it is, and how to get to the next state.
whats this got to do with  coroutines, well what we use this to break up code. once its broken up we can swap back and forth between all the different jobs we have to do. 
like spinning plates, we go round each in turn keeping them stable. 

![ oh Salem ](https://i.giphy.com/media/EndmKkbSJeFwY/giphy.webp)

## I yield my time
so now we know that we can write code that can get split up. we need to tell it where to split though as the computer cant guess, it doesn't know when would be safe.
roll on the yield key word. this is the magic incantation to say I'm done for now. if Its gotten to a state that is of use elsewhere it may even yield return, here's what I've got so far if you will.

## Unity Time
till now its been a bit abstract, but now bringing it together. Unity  coroutines have functions avalable in them like WaitForSeconds(s). this lets your function set an alarm to continue execution later.

![ alarm clock ](https://i.giphy.com/media/gBW8Qgfaa2ije/giphy.webp)

here's an example of how to set this type of alarm.

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