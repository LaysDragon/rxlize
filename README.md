# Rxlize

Rxlize is a library for manage state, asynchronous task and others actions in reactive (RxJS) way.

## Install

```
npm install rxlize
```

```
yarn add rxlize
```

This is a preview version, functions in this library not yet cover by test, so take your own risk.

## List of function

- State
  - `rxStore` -- Create a simple store that can dispatch action to update.
  - `rxToggle` -- Create a boolean state that provide `on`, `off`, `toggle`, `next` to change the state.

- Side Effect
  - `rxAsync` -- Handle an async process and provide loading state and error stream.
  - `rxNext` -- Special case of `rxAsync` which provide a default `Subject`.

- Angular
  - `rxNgLifecycle` - Transform Angular component lifecycle event to observable stream.