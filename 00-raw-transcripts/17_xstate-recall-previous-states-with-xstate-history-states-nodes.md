Instructor: [00:00] Inspired by the cooler weather, I have a space heater machine. It has two top-level states, powered off and powered on. When we're in the powered on state, we have two levels of heat -- we have low and we have high.

[00:11] It sure would be nice if my space heater would remember what setting I was on the next time that I power it back on. We can do this by using history state nodes. We add a history state node by defining the type as history. This creates a state node that when transitioned to will return to the previous state of this area of the machine.

[00:36] In this case, that means the previous state underneath the powered on state. In order to trigger this transition, we'll need to actually set toggle power here not to powered on, but to the specific history state node by using dot notation.

[00:52] We can update our machine, and we now see that toggle power actually goes directly to this history state node. By default, if history doesn't have a previous state to go to, it'll go to the initial state of that area.

[01:05] When we click toggle power, it goes to the low state. If I switch it to high, and then I toggle it off, when I click toggle power again, we'll go to that history node, and it remembers that I was in the high state.

[01:20] What this history node has done is remembered a shallow history of our powered on state. Let's change our example up a bit and create several states underneath powered on using parallel states.

[01:33] I'll move low and high to a heated state node, and I'll create enabled and disabled state nodes in our oscillating state node. Then I'll move my history state node as one of the parallel states. I'll update my machine, and we'll now see that I have parallel states of heated and oscillating. When I toggle the power on, I'm in low heat and I've disabled oscillation.

[01:59] Now by default, if I change these settings, and I toggle this off, it won't remember that I was in high heated and enabled oscillating. The reason for this is by default, this history is shallow. We can enable the ability for it to remember all child states and set them by setting this to deep.

[02:18] If we update our machine now, we can toggle power on. If we switch these to various settings, in this case, high and enabled, and we toggle power off and we toggle it back on, because of that deep setting, it remembers where we were in the child states of powered on.
