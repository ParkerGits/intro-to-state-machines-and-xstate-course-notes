Instructor: [00:00] Using machine.transition to change state is useful, but it's tedious. We need a way to instantiate a machine that maintains its state and allows us to send events and more to it. To do this, we'll use the interpreter xState provides for us, interpret.

[00:14] I will require that function as well. The return value from an interpreted machine is known as a service, so I'll call this service. A service will maintain the state of our machine as it transitions from state to state, but it won't do anything until we start the service.

[00:29] Once we've started the service, we can send events. Sending an event returns us the next state, so we can actually save it and log out that object. We can see that it changed to the value lit. However, we don't need to save the next time every time we send.

[00:44] We can also use the state getter on the service and see what the current state is. Again, the value is lit. It's the same state object, so that makes sense. However, this can't be the most useful way to log out the next state of our service. There's got to be a better way, and there is.

[01:00] There are many methods that allow us to add listeners to our service and respond to changes to it. The most useful one to us is the onTransition method. onTransition takes listener function that receives a state argument.

[01:13] This is always sent the next state of the machine, and we can move our logging action to there. Now, each time that we send an event to our service, we'll see a value logged out for it in the console. We can also utilize some of the information from the state object itself here to limit our logging.

[01:32] For instance, we can check and ensure that the state has actually changed before logging. I'm going to remove the type of final from our broken state to be able to send the break event twice. Notice that broken was only logged out once.

[01:47] How about, instead of seeing that a state is changed, we check to see if a state matches a particular value and only log out when that happens? We can see that we only logged out, "Yo, I'm broke," when we were in the broken state.
