---
layout: default
title: Module bract.ring - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | [About](/about.html) | [Documentation](/documentation.html) | [Discuss](/discuss.html)

## Module: bract.ring

Clojars coordinates: `[bract/bract.ring "0.3.1"]`


### Context keys

| Context key                | Value                        | Description |
|----------------------------|------------------------------|-------------|
| `:bract.ring/ring-handler` | `(fn [request]) -> response` | Ring handler function |


### Inducers

All inducers exposed by _bract.ring_ are in the namespace `bract.ring.inducer`. A summary is below:

| Inducer function  | Input context keys         | Output context keys        | Description |
|-------------------|----------------------------|----------------------------|-------------|
| `apply-wrappers`  | `:bract.ring/ring-handler` | `:bract.ring/ring-handler` | Apply Ring wrappers |


### Entry points

This module provides entry points for development purpose.

To integrate with [lein-ring](https://github.com/weavejester/lein-ring) put the following in your `project.clj`:

```clojure
:plugins [[lein-ring "0.12.0"]]
:ring {:port    3000                      ; <- optional
       :nrepl   {:start? true :port 3001} ; <- optional
       :handler bract.ring.dev/handler
       :init    bract.ring.dev/init!}
```


<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
