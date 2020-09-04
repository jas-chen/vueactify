# vueactify
> Reactive React components, powered by [@vue/reactivity](https://www.npmjs.com/package/@vue/reactivity).

## Installation

```
yarn add vueactify
```

## Usage

Clock example

```js
import React from "react";
import { ref } from "@vue/reactivity";
import R, { Effect, useForceMemo } from "vueactify";

const App = () => {
  return useForceMemo(() => {
    const time$ = ref(new Date().toLocaleTimeString());
    let intervalId;

    return (
      <>
        <Effect>
          {() => {
            intervalId = setInterval(() => {
              time$.value = new Date().toLocaleTimeString();
            }, 1000);

            return () => clearInterval(intervalId);
          }}
        </Effect>
        <R>{time$}</R>
      </>
    );
  });
};

export default App;
```

[TodoMVC](./examples/TodoMVC/index.js)
