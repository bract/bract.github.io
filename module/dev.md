---
layout: default
title: Module bract.dev - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/)    |    [About](/about.html)    |    [Documentation](/documentation.html)    |    [Discuss](/discuss.html)

## Module: bract.dev

Leiningen coordinates: `[bract/bract.dev "0.3.1"]`


### Usage

Include it as a dev dependency in your `project.clj`:

```clojure
:profiles {:dev {:dependencies [bract/bract.dev "0.3.1"]
                 :source-paths ["dev"]}}
```

Also create a file `dev/user.clj` as follows:

```clojure
(ns user
  (:require
    [bract.core.dev   :refer [start stop verbose config]]
    [bract.dev.reload :refer [go reinit reset restart]]))
```

Now when you run `lein repl` you have access to the `user` namespace vars.


### Keys

This module does not expose any context/config keys.


### Inducers

This module does not expose any inducers.


### Entry points

This module exposes several functions as entry point for REPL based interactive development. These functions are
available in the `bract.dev.reload` namespace:

| Function call | Description |
|---------------|-------------|
| `(reinit)`    | De-init application, then code reload followed by init |
| `(reset)`     | Stop application, followed by re-init |
| `(go)`        | Same as `reset` |
| `(restart)`   | Stop application, then re-init followed by starting app |

<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
