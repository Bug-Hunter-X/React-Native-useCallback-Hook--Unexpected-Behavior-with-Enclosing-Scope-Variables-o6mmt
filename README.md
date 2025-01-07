# React Native useCallback Hook Bug: Enclosing Scope Variable Issue

This repository demonstrates a subtle bug related to the `useCallback` hook in React Native. When a memoized callback function accesses a variable from its enclosing scope, and that variable changes, the callback might not reflect the updated value, leading to unexpected behavior.  This example highlights the problem and provides a solution.

## Bug Description
The `useCallback` hook is meant to optimize performance by preventing unnecessary re-renders. However, if you don't correctly manage dependencies, this optimization can hide a crucial issue.  If you omit a variable from the dependency array that the callback depends upon, the callback will not update when that variable changes, causing it to always use the initial value of the variable.

## Solution
The solution is to include all variables that are accessed within the callback function in the dependency array. This ensures that the callback is updated whenever any of those variables change.