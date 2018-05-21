---
title: How Redux work ?
tags: [Redux, ReactJS]
date: 2018-04-02 22:35:58
---

If you want to understand how Redux work, `createStore(reducer)` is the core function you should know and try to implement yourself. Here is a basic example of Redux, don't worry I will break it down later :
<!--more-->

```javascript
const counterReducer = (state = 0, action) => {
    switch (action.type){
        case 'INCREMENT':
            return state+1;
        default :
            return state;
    }
}
const store = createStore(counterReducer);
const render = () => document.body.innerText = store.getState();
store.subscribe(render);
render();
document.addEventListener('click', ()=>{
    store.dispatch({type: 'INCREMENT'})
})
```

## What is Reducer ?

`Reducer` is a pure function, take `state` and `action` as parameter and return new state.

```javascript
const counterReducer = (state = 0, action) => {
    switch (action.type){
        case 'INCREMENT': 
            return state+1;
        default :
            return state;
    }
}
```

## What is Store ?

`store`, which return from `createStore(reducer)` has three method, `getState()`, `subscribe(listener)` and `dispatch(action)`

```javascript
const createStore = (reducer) => {
    const getState = () => (...)
    const dispatch = (listener) => (...)
    const subscribe = (action) => (...)
    return { getState, dispatch, subscribe }
}

```

### getState

 `getState()` is a simple function return `state`

```javascript
const getState = () => state;
```

### subscribe(listener)

`subscribe(listener)` is a function to register `listener`, it simply put `listener` in a stack, in ReactJS we usually put `render` function as a `listener`.

```javascript
const subscribe = (listener) =>{
    listeners.push(listener);
}
```

### dispatch(action)

`dispatch(action)` is a function trigger `reducer` to compute new state then trigger each subscribed `listener`

```javascript
const dispatch = (action) => {
    state = reducer(state, action);
    listeners.forEach(listener => listener());
}
```

## A simple version of Redux

Combine function above we got a simple version of Redux :

```javascript
const createStore = (reducer) => {
    let state;
    let listeners = [];
    const getState = () => state;
    const dispatch = (action) => {
        state = reducer(state, action);
        listeners.forEach(listener => listener());
    }
    const subscribe = (listener) =>{
        listeners.push(listener);
    }

    dispatch({})
    return { getState, dispatch, subscribe }
}

const counterReducer = (state=0, action) => {
    switch (action.type){
        case 'INCREMENT': 
            return state+1;
        default :
            return state;
    }
}

const store = createStore(counterReducer);
const render = () => document.body.innerText = store.getState();
store.subscribe(render);
render();
document.addEventListener('click', ()=>{
    store.dispatch({type: 'INCREMENT'})
})
```

## Reference

https://egghead.io/courses/getting-started-with-redux