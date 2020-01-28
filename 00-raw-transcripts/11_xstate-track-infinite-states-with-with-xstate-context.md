Instructor: [0:00] Not all states can be represented as a set of finite states. Some things are infinite states. In XState, this is considered context or called extended state. I have a lightbulb here that I'm calling a multicolored ball because I'd like it to act like a modern lightbulb that can change colors.

[0:18] We can do this with context. We add context as an object on our machine configuration. In this case, I'll give it a property of color which I'll set initially to white. We're going to update our machine, and nothing has changed about our visualization.

[0:35] When I select state tab, we currently have a context of color. We can make updates to our color by creating actions called assign. I'm going to add an event on the lit state called change color. Change color will not change the state of the lightbulb, so we don't need to give this a target.

[0:53] We'll add the actions property. We can use our assign function here. Assign has two signatures. It can receive an object of key value pairs. In this case, we could set color straight to red for example. We can update the machine. We see that we now have a new event.

[1:13] We even see what color that this assign will set it to. It says that it sets to red. We'll toggle the lit. We'll call change color. We'll go to our state tab and we'll see that it's currently red. We'll go back to definition and reset the machine.

[1:28] We can also use this key value pair and provide a function to the value that receives the current context, the event object, in this case change color. We can assign it based on values from there. In this case, I might want to send a color on the event itself and assign that instead.

[1:50] From the advanced tab, I can call toggle to get to the lit state. We have change color available. We'll select change color. We can add a color of, let's make it green. We've called the change color event. We could see that the color was updated to green. In fact, if we hover over this, we could see the exact function we assigned it to, context event returns event color.

[2:14] Assign can also take a function as its argument. In this case, the function receives the current context, the event, and returns an object to be merged in with the next context. We can update our machine, toggle the lit, and we can call change color event again with a color set. This case, let's make it blue. Once again, our state has updated correctly.

[2:38] Notice that when I hover over assign with this format, I can't see the function that I was called. It is generally preferred to call assign with the object signature. There's one last way that we can add this action. Rather than defining it inline here, we can define it on the second argument to machine, the options object.

[2:58] We'll define an actions key here and create a method that will be this action. In this case, we'll call it change color. We could take this function from up here, cut it out, call the change color method from here, and paste this back in here. We can update our machine and see that change color has now replaced our assign, as it now has a name.

[3:22] We'll toggle again to lit, go to the events tab, select change color. This time, we'll make it black. I don't know how a black light would work this way, but maybe it would. We send the event. We could see that the state updated to black.
