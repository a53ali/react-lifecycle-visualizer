# React Lifecycle Visualizer

## Usage

The panel shows the new React 16.3 lifecycle methods, unless the component defines at least one legacy method and no new methods. On a component that has both legacy and new methods, React ignores the legacy methods, so the panel shows the new methods.

Though technically not lifecycle methods, `setState` & `render` are also traced. A single `setState(update, [callback])` call may generate up to three log entries:

  1. `'setState'` for the call itself.
  2. If `update` is a function instead of an object, `'setState:update fn'` is logged when that function is evaluated.
  3. If a `callback` function is provided, `'setState:callback'` is logged when it's called.

To save space, the lifecycle panel only contains `setState`, which gets highlighted on any of the three events above.


## Run the demo locally

To run a local copy of the StackBlitz demo, simply clone the repo, and run `npm install` & `npm start`:

```
cd react-lifecycle-visualizer
npm install
npm start
```

The demo runs on http://localhost:8000/.

## Use webIDE
Navigate to https://stackblitz.com/github/Oblosys/react-lifecycle-visualizer/tree/master/examples/parent-child-demo?file=src/samples/New.js

## Tutorial
Once your app is up and running, let's get started! 
If you are working in pairs, then for each step, please alternate!
Example: step 1 was lead by person A, step 2 should be led by person B.

Pre-requisite:
* What is state? State is a plain JavaScript object used by React to represent an information about the component's current situation. 
It's managed in the component (just like any variable declared in a function).
It’s not mandatory to use States and since it increases complexity, a stateless component is always preferable. This however is inevitable in an interactive app.
* Basic understanding of React.
* How does `setState` works? https://reactjs.org/docs/react-component.html#setstate

Step 1:
Go to https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/
* The goal here is to build a basic understanding of component lifecycle. 
Start with show less unchecked and click into the blocks to understand what each function does.
* Once you are comfortable. check show less and build and understanding of the new functions available to you.

Step 2:
Navigate to `/examples/parent-child-demo/src/samples/New.js` and take a few minutes to understand the code itself.
* The goal here is to understand all the states that are managed.
* Understand the components that are involved and getting comfortable with the code.

Step 3:
Let's bring it all together! In this step please focus on the child in the app and increment y.
* The goal here is to focus on the leaf node or child. 
* Is it clear why incrementing y is triggering the functions like render in the app?

Step 4:
Let's get the party started! In this step, let's switch focus to the parent and increment x.
* The goal here is to understand the side effects when updating the parent's state.
* What function can we implement to prevent the child from updating when x is updated?
* What function can we implement to prevent the child from updating when x is even? 

Before moving on, comment out the function that you override in step 4.

Step 5:
Living on the edge I see! You survived this far! In the child, increment x and y!
* What is happening here? Can you explain the logs to your partner?

Step 6:
Damn, you are still here? Good job! Let's focus on `componentDidMount` and add the following code to the function
```
setTimeout(() => {  
       this.incY();
 }, 3000);
 ```
 * The goal here is to understand `componentDidMount`.
  This snippet is quite common and can you spot the side effect of setting state in `componentDidMount`?
  Hint: what are we triggering multiple times?
 * Now that you understand the possible side effects, what are the possible use cases to use `componentDidMount`? 
 Hint: Think about data and page load.
 
 Step 7:
This one should be easy! `componentDidUpdate` is another useful method but then again every function is useful and just like a hammer, it can be useful and dangerous.
* The goal here is to understand `componentDidUpdate`.
* When is this method useful and how can you leverage the parameters?
Hint: Step 6... I guess if you skipped step 6 this isn't helpful.

Step 8:
This one is a doozy. `setState` clearly has many side effects. 
Given all the methods available to in a react component lifecycle, in the child component in `New.js` add all the methods and why or why not `setState` can be used.
* The goal here is to understand `setState` and the possible usage of this method in the lifecycle methods.

Highly recommend joining https://www.reddit.com/r/reactjs/ if you are passionate about react!