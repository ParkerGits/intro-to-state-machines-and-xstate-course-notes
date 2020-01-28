Instructor: [0:00] Here I have your basic stop light machine with three states -- red, green and yellow. We transition between those states with a simple timer event. Now triggering these events manually, and I don't just mean with a mouse, it's a little tedious when we know that a light can just happen after a certain amount of time is passed.

[0:18] Wouldn't it be nice if we could delay transitions and events in xstate? We can. Very simply, we're going to remove the onProperty and replace it with after. We can replace the event name with the number of milliseconds we'd like to transpire before we take the transition.

[0:36] For the sake of this video, I'll make some of the shortest durations of stop lights you've probably ever seen. A green light will only last three seconds. A yellow light, one second. The red light, four seconds.

[0:49] We'll update our machine and we could see that the timers have automatically started. Each time the timer is hit, we take the transition to the next state. It might be nice if we would give these times their own identifying names so that read a little bit nicer in the state chart.

[1:04] We can do this with the second argument to machine, the options object and define our delays. I am going to set the green timer to 3,000, the yellow timer to 1,000, and the red timer to 4,000. Then in my machine, I'm going to replace this with green timer, yellow timer, and red timer.

[1:26] We update our machine. We now see that our events have updated though their times are the same. What's nice about doing this way is we can read this very clearly. The green timer happens, and then we go to yellow, and we can modify these. We can make these times dynamic if we'd like.

[1:44] We can actually set each of these as the result of a function that receives context and event. For instance, what if during rush hour we added a co-efficient that we could multiply these by? Maybe something that look like this.

[1:58] I am just going to copy-paste this into the other one. Now, let's add this to context. By default, we'll set it to one. We'll update our machine. We'll see that the time doesn't change because we're multiplying by one.

[2:12] If we add a way to update this context, we'll see that the timers change. Let's add an onEvent to the top level of our machine since we want to respond to it in any of the states that we're in. Now we need to add the increment rush hour action to our machine's configuration. I'll add that down here in actions. This will be in a sign that will set the rush hour multiplier to its current context value plus one.

[2:42] We'll update our machine and we'll see that we have added an increment rush hour event to our whole machine. I'm going to go the state tab really quick. I'm going to hit increment rush hour. We'll see that it's by two. You can actually see that the timers take twice as long.

[3:00] If I increment it again, maybe traffics are really heavy and we want to let them go by for long time, I can increment it to three and you can see that the timers are going even slower. We can actually see it down here the delay has been set to 9,000 for green, 3,000 for yellow, and it should 12,000 for red.
