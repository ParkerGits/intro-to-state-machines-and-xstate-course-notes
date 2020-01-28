Instructor: [00:00] Here I have a state machine called cuteAnimalsMachine because who doesn't like some cute animals. I want to be able to fetch some animals. When they load, I want to know when it's successful to go to the success state over here or if it fails go to the failure state and give me the option of retrying.

[00:17] How can I do this with XState? You might notice that a promise looks a lot like a state machine itself. In fact, every promise can be represented as a state machine, with idle, loading, success, and failure states.

[00:30] Because of this fact, we can invoke promises when we enter a state. I'm going to quickly write a promise to get some cute animals from Reddit. Man, that's a lot of data properties for Reddit JSON.

[00:43] Now we went to fetch that when we call this fetch event. When we call fetch, we'll transition to loading. Inside of loading, we're going to invoke our promise. We do this by using the invoke property. We can give this invocation an ID. In this case, I'll give it the ID of fetchCuteAnimals.

[01:03] We'll give it a source. In this case, it's the promise function we have up above. This is fetchCuteAnimals. Promises will respond to two specific events, onDone when they resolve and onError when they reject.

[01:19] We'll write the onError object first. In that case, we want to target failure as our transition, and we want to take some actions. Namely, we want to update the error in context. I'll just write that inline here. With promises, the error is returned on the data property of the event object.

[01:39] Now we'll write our onDone object. In this case, we'll target the success state node. We'll also take the action of assigning the cute animals in context. The data returned from resolve is also put on the data property of the event object.

[01:56] From here, we can update our machine. We could see it got a whole lot more complicated but a whole lot more useful. When we're in the idle state, we'll trigger the fetch. You see that the promise immediately resolved to success because it worked.

[02:10] I'm going to reset the machine really quickly. Let's just say, for good measure, that our fetchCuteAnimals doesn't work. We'll comment this out really quick. We'll return a promise reject, just to show that will go to the failure state.

[02:25] Notice it failed immediately. We're in the failure state. We hit retry. We know that's going to continue to fail. Removing this and uncommenting this, we'll update our machine one more time. We could see that when we fetch, our state is updated, and all our cute animals are in context.
