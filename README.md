# pinkbox-react

Basically is customized clone of the [red box](https://github.com/KeywordBrain/redbox-react) (aka red screen of death) renders an error in this “pretty” format:

<img src="http://i.imgur.com/9Jhlibk.png" alt="red screen of death" width="700" />

## Usage
Catch an error and give it to `pinkbox-react`. Works with
* [react-transform-catch-errors](https://github.com/gaearon/react-transform-catch-errors) ([see example](https://github.com/KeywordBrain/redbox-react/tree/master/examples/react-transform-catch-errors) or [react-transform-boilderplate](https://github.com/gaearon/react-transform-boilerplate/))
* [babel-plugin-react-hot](https://github.com/loggur/babel-plugin-react-hot) & [babel-plugin-react-error-catcher](https://github.com/loggur/babel-plugin-react-error-catcher) (see [example](https://github.com/KeywordBrain/redbox-react/tree/master/examples/babel-plugin-react-hot))
* [react-hot-loader](https://github.com/gaearon/react-hot-loader) (deprecated! see [example](https://github.com/KeywordBrain/redbox-react/tree/master/examples/react-hot-loader-example), relies on changes in unmerged [pull request](https://github.com/gaearon/react-hot-loader/pull/167) and will not be merged!)

or manually:

```javascript
const PinkBox = require('pinkbox-react')
const e = new Error('boom')
const box = <RedBox error={e} />
```

Here is a more useful, full-fleged example:

```javascript
/* global __DEV__ */
import React from 'react'
import App from './components/App'

const root = document.getElementById('root')

if (__DEV__) {
  const RedBox = require('redbox-react')
  try {
    React.render(<App />, root)
  } catch (e) {
    React.render(<RedBox error={e} />, root)
  }
} else {
  React.render(<App />, root)
}
```

## What is this good for?
An error that's only in the console is only half the fun. Now you can use all the wasted space where your app would be if it didn’t crash to display the error that made it crash. You should use this in development only.

## Will this catch errors for me?
No. As you can see above, this is only a UI component for rendering errors and their stack traces. It's works great with other solutions, that automate the error catching for you, see the [examples](https://github.com/KeywordBrain/redbox-react/tree/master/examples).
