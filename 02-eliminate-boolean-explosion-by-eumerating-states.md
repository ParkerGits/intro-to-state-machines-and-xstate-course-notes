[Video Link](https://egghead.io/lessons/javascript-eliminate-boolean-explosion-by-enumerating-states)

# 02. Eliminate Boolean Explosion by Enumerating States

To follow along with this lesson, I copy the code found in the "before.js" file found in the GitHub link in the description of the lesson.

In the lesson, Kyle has written a function that simulates the functionality of a lightbulb:
```js
function lightBulb() {
  let isLit = false
  let isBroken = false

  return {
    state() {
      return { isLit, isBroken }
    },
    toggle() {
      isLit = !isLit
    },
    break() {
      isBroken = true
    }
  }
}

const bulb = lightBulb()

const log = () => {
  console.log(bulb.state())
}

bulb.toggle()
bulb.break()
```
He shows us, however, that it is easy to get into an "impossible state," in this case a state where the lightbulb is both broken and lit:
```
node index.js
-> { isLit: true, isBroken: true }
```
The first solution he enacts in his code is a "guard" against this impossible state by both guaranteeing
that the "isLit" boolean is false when "isBroken" is true and returning this state early:
```js
function lightBulb() {
  let isLit = false
  let isBroken = false

  return {
    ...
    toggle() {
      if(isBroken) {
        isLit = false
        return
      }
      isLit = !isLit
    },
    break() {
      isBroken = true
      isLit = false
    }
  }
}
```

**Resources**

[More information on State Machines from the instructor](https://kyleshevlin.com/tags/state-machines)

[State Machines Podcast from Syntax](https://syntax.fm/show/206/state-machines-css-and-animations-with-david-k-piano)