---
title: ReactJS performance tuning tips
date: 2018-04-02 00:30:11
tags: [ReactJS, Performance Tuning]
---

1. Use `React.PureComponent`, it implement `shouldComponentUpdate()` by shallow compare prop and state, it is powerful with [Immutable.js](https://github.com/facebook/immutable-js).
1. Use [Chrome extension](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) and checked `highlight updates` in dev tool to find any unnecessary updates.
1. Use [React-virtualized](https://github.com/bvaughn/react-virtualized) for render huge list in small chunk at a time.
1. Use `Production build`, for example with webpack you need following config:
    
    ```javascript
    new webpack.DefinePlugin({
        'process.env.NODE_ENV': JSON.stringify('production')
    }),
    new webpack.optimize.UglifyJsPlugin()
    ```