# React useEffect Infinite Loop Bug
This repository demonstrates a common mistake in React's `useEffect` hook that can lead to an infinite loop. The bug is caused by incorrectly adding the state variable as a dependency, resulting in the useEffect function running continuously.

## Bug Description
The `MyComponent` function uses `useState` to manage a count. The `useEffect` hook attempts to increment the count. However, because `count` is included in the dependency array, the effect runs after every state update, causing a continuous loop and crashing the application.

## Solution
The solution involves fixing the dependency array to not include the state variable that is being updated directly within the effect. In this case, an empty array `[]` should be used, and any side effects that depend on external data should be included. It's important to note that an empty array means that the effect runs only once after the component mounts, which is often what's desired when initializing a component or fetching initial data.