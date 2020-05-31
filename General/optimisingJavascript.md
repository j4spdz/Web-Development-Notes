<!-- omit in TOC -->
# Optimising Javascript

<!-- omit in TOC -->
## Contents

- [Code Splitting](#code-splitting)
- [Tree Shaking](#tree-shaking)
  - [Reduce JavaScript Payloads with Tree Shaking](#reduce-javascript-payloads-with-tree-shaking)
- [Avoid blocking main thread](#avoid-blocking-main-thread)
- [Avoid Memory Leaks](#avoid-memory-leaks)
- [Avoid Multiple re-render such as in React](#avoid-multiple-re-render-such-as-in-react)
  - [1. Performance metrics](#1-performance-metrics)
  - [2. React Developer Tools(Chrome Extension)](#2-react-developer-toolschrome-extension)
  - [3. Render update only when are changes](#3-render-update-only-when-are-changes)
    - [ShouldComponentUpdate](#shouldcomponentupdate)
    - [PureComponent](#purecomponent)
  - [4. Beware: React setState is asynchronous](#4-beware-react-setstate-is-asynchronous)
    - [Wrong](#wrong)
    - [Correct](#correct)

## Code Splitting

[Comparison of loadble-components with React.lazy](https://loadable-components.com/docs/loadable-vs-react-lazy/)

Breaks .js into chunks. Use **@loadable-components** or **React.lazy**
Note that Suspense is not yet available for server-side render

```Javascript
import { lazy } from '@loadable/component'

const OtherComponent = lazy(props => import(`./${props.page}`))

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <AsyncPage page="Contact" />
      </Suspense>
    </div>
  )
}
```

## Tree Shaking

Done behind the scene by webpack. Remove any unused code when you build your app

### [Reduce JavaScript Payloads with Tree Shaking](https://developers.google.com/web/fundamentals/performance/optimizing-javascript/tree-shaking/)

JavaScript is an expensive resource to process. Unlike images which only incur relatively trivial decode time once downloaded, JavaScript must be parsed, compiled, and then finally executed

When your app is young, you have less dependencies and be using most of them. As your app ages, however, more dependencies can get added and older dependencies may fall out of use but not get pruned from your codebase. The end result is that an app ends up shipping with a lot of unused JavaScript.

Tree shaking addresses this by taking advantage of how we use static import statements to pull in specific parts of ES6 modules.

## Avoid blocking main thread

Minimise javascript files and execution time. Be smart on how much javascript we are including in the code. Justify reasons for using libraries like jQuery over native codes

## Avoid Memory Leaks

Making sure that we do not keep adding memory to our app

## Avoid Multiple re-render such as in React

Minimise the number of DOM manipulation on the browser

### 1. Performance metrics

- Append **?react_perf** to your local server URL (e.g. localhost:3000/?react_perf) and visit that URL in a browser
- view at performance tab in chrome developer tools

### 2. React Developer Tools(Chrome Extension)

Highlight updates to check which element is updated unnecessarily

### 3. Render update only when are changes

>Why did you render: npm library that tells you in the console during development when there's an unnecessary re-render

#### ShouldComponentUpdate

Use this cautiously and not overused as you are runnning another function before render. Measure how it is as it may hinder performance
Only update when the state changes instead of re-render everytime

#### PureComponent

Component will only render when the props change. However, it only use shallow comparison for props and may miss some changes for complex data structures like deeply nested list

### 4. Beware: React setState is asynchronous

#### Wrong

Invalidating state changes is one issue here. Another is that you may be acting on an outdated view of the current state. Any time you access this.state you can not be sure that it’s the most recent version. This is especially important if you do state changes such as incrementing or appending:

```Javascript
// Increment foo
this.setState({ ...this.state, foo: this.state.foo + 1 });
// Append an item to an array
this.setState({ ...this.state, foo: [].concat(this.state.foo, 1) });
```

These state changes must be done atomically and you must be sure that you are basing your decisions and actions on the current view of the state.

#### Correct

```Javascript
this.setState((previousState, currentProps) => {
    return { ...previousState, foo: currentProps.bar };
});
```

Writing the callback inline like that is convenient, but it doesn’t completely prevent the problem from happening. It is still possible to write the callback such that it returns the new state based on a potentially outdated view of the current state, namely when you capture values from the state outside of the callback:

```Javascript
// Capturing values from the state outside of the setState callback.
let previousFoo = this.state.foo;
this.setState(function incrementFoo(previousState) {
    // BAD! Setting `foo` based on a potentially outdated
    // view of its current value: `foo` may have been updated
    // in the meantime by another call to `setState`.
    return { ...previousState, foo: previousFoo + 10 };
});
```

We're used to calling setState with one parameter only, but actually, the method's signature support two. The second argument that you can pass in is a callback function that will always be executed after the state has been updated (whether it's inside React's known context or outside of it).

```Javascript
_onClickHandler: function _onClickHandler() {
   console.log('State before (_onClickHandler): ' + JSON.stringify(this.state));
   this.setState({
   dollars: this.state.dollars + 10
   }, () => {
   console.log('Here state will always be updated to latest version!');
   console.log('State after (_onClickHandler): ' + JSON.stringify(this.state));
   });
}
```
