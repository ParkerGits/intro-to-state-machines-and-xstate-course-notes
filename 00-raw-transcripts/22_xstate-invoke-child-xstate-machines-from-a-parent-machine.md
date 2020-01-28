Instructor: [00:00] Here, I have a machine that I am calling parent with states of idle, active, and done. It starts in the idle state. We can see an activate event sends it to the active state. I haven't written a way for it to go from active to done. That is because in the active state, I would like to invoke another machine and let that machine determine when I move to the done state.

[00:22] Up here, I've written a second machine. This is child machine. It has several steps of states. Step one, step two, and step three, and we can step through them to get to the final state.

[00:33] I can invoke this machine from a state within the parent machine by using the invoke property. We'll give an ID, set to child, and a source of child machine. When we enter the active state, it will invoke this child machine and it will start it in its initial state.

[00:52] Let's update the machine. We could see that invoke child has been updated. We go to state, we're currently in idle. Let's activate it. When we get into the value active, that is the state of active, we can see that we now have a child state as well. We're in the value of step one.

[01:10] Currently, xstate-viz doesn't support showing the child machine as well. We'll rely on the state panel to indicate where we are in the child machine. Right now, I have no way of sending events to this child machine. How can I do that?

[01:26] In the active state node of the parent machine, I am going to add the onProperty to send events. I'll create an event step. On this event, I'd like to have an action occurred, which is I want to send a step event to my child machine. We'll update the machine.

[01:47] We can see now that when we're in active, we have the step event available to us. Let's open up the state panel really quick and let's send that step event. We can see that we send a step event to the child and the child is now in step two.

[02:04] If I hit the step event again, I get to step three. Step three is a final state for the child machine. How do we want to respond to that in our parent machine?

[02:15] We can do that under the invoke property with the onDone property. This will fire whenever the child machine reaches a final state. When our child machine is finished, in a final state, we'd like to go the done state in our parent machine.

[02:32] We update our machine. I am going to back to the state tab again. We'll activate it. The child machine has been invoked. We can see down here. It's at value of step one. We send a step event to our parent machine, which sends it to our child machine, and we're now in step two.

[02:51] When we send a step event again, our child goes in the step three, which is the final state. That final state triggers the onDone and moves us into the done state.
