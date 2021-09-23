---
layout: cover
---

# Tree shaking with side-effects

![Local Image](/tree.png)

<!-- 
You can imagine your application as a tree. The source code and libraries you actually use represent the green, living leaves of the tree. 

Dead code represents the brown, dead leaves of the tree that are consumed by autumn. In order to get rid of the dead leaves, you have to shake the tree, causing them to fall. 

* Dead code elimation - decrease size of your app
-->

---
layout: fact
---

```js {monaco}
import { groupBy } from "lodash";

export function crazyStuff() {
  groupBy();
}
```

<!--
tree shaking goes well with es2015 modules
commonjs modules doesn't work with tree shaking
-->

---
layout: center
---

package.json

```js {3}
{
  "name": "is-array",
  "sideEffects": true,
  "scripts": {
    "build": "webpack --mode=production --node-env=production",
    "build:dev": "webpack --mode=development",
    "build:prod": "webpack --mode=production --node-env=production",
    "watch": "webpack --watch",
    "start": "node dist/main.js"
  },
  "devDependencies": {
    "@babel/core": "^7.15.5",
    "@babel/preset-env": "^7.15.6",
    "babel-loader": "^8.2.2",
    "webpack": "^5.53.0",
    "webpack-cli": "^4.8.0"
  }
}
```

<!-- 
* Side effects - specify that module doesn't contain side effects to further optimize tree shaking
* Hint to the webpack compiler to specify which module is pure (doesn't contain side-effects) so webpack can safely prune code that is unused.
* When side effects are not set, then webpack uses other techniques to detect which code can be safely removed but this is not as efficient as explicitly specyfing sideEffects.
* Not only mark your whole package free from side-effects, you cam mark invidividual files or even functions.
* So what let's set sideEffects to false in every package.json and voila we are set. Unfurtently it's not so easy. You must know if the code is really free from side-effects, otherwise this can cause unexpected behaviour, that can affect logic of your app.
-->

---
layout: center
---

# What is side-effect?

<!--
In general something that performs externally visible behaviour when the module is loaded

Types of side effects:
* mutating global objects (window)
* event handlers
* pollyfils as they are usually affecting global scope and usually not provide an export
-->

---
layout: center
---

```js
window.myValue = "So much wow";
```

<br/>
<br/>

```js
export function setValue() { // not a side effect!
  window.myValue = "So much wow"; 
}
```

<!--
Example - external state
-->

---
layout: center
---

```js
window.onload = () => console.log("fancy code");
```

<!--
Example - event handler
-->

---
layout: center
---

```js
window.fetch = () => "amazing fetch logic";
```

<!--
Example - window.fetch pollyfil
-->

---
layout: center
---

# Demo

<!--
* If your library doesn’t include side effects, set sideEffects: false in its package.json.
* If your library does include side effects, you can still enable as much tree-shaking as possible. List the files with side effects explicitly, or use inverse globs to list the paths that don’t have side effects.

Example:
* how sideEffects affects bundle size (tree shaking lodash)
* how sideEffects can affect logic of your app
-->
