Instructor: [00:00] Here I have an Echo machine with only one state, listening. The idea of this machine is when the event speak is called, I want to set up a callback that'll send Echo events back to my machine if, and only if, the right type of event is sent. We can do this by invoking a callback as a service.

[00:20] To start, I'm going to add the invoke property on the listening state node. Invoke takes an ID and takes a source. This source should be a Callback Handler. I'm going to call it Echo Callback Handler. We'll write that function now.

[00:38] Echo Callback Handler is a function that receives the context and event that invoked the service. In this case, it'd be the initial context of our machine, which is undefined. The event would be the initialization of the machine.

[00:51] This function returns another function. This is where we manage our callback service. This function receives two arguments, a callback function that we can use to send events back to the parent machine, and an onEvent function that we can use to respond to specific events in the machine.

[01:09] Just for the sake of the concept, I want to respond to any event sent to my Callback Handler, so we'll add onEvent. This receives a function that receives that event. Inside here, I'm going to call this callback with Echo. This callback will send an echo event to the Echo machine anytime an event is sent to our callback service.

[01:35] How do we send events to our callback service? onSpeak, I'm going to add the actions property. I'm going to use the send action creator. This is a function that receives an event. In this case, it can be anything. What's important is that we add the options object, the second argument, and say where to send it to.

[01:57] I'm going to send it to the ID of my callback service, Echo callback. This will send the EventFoo to the service Echo callback. That'll be received by this onEvent function. onEvent will trigger the callback of Echoback, which will lead to the Echo event being handled in the listening state, which should log out EchoEcho.

[02:22] I'm going to update my machine. I'm going to open the console. We're going to send the event. You could see, when we send it, the Echo event is sent in the callback and the actions are triggered.

[02:38] To take this a step further, I'd like to only respond this Echo callback when the event is of a certain type. I'm going to say, if event type equals hear, as in, I want to hear this thing, then callback Echo. Going to update my machine. We're still sending Foo to Echo callback.

[03:02] If I open up the console and I send the speak event, which sends the FooEvent to my Callback Handler, we'll see that it doesn't echo. If we update this to the type hear, and update the machine, we now see that it works again.
