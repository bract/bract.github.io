---
layout: default
title: Module bract.ring - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | [About](/about.html) | [Documentation](/documentation.html) | [Discuss](/discuss.html)

## Module: bract.ring

Clojars coordinates: `[bract/bract.ring "0.6.0-0.1.0"]`


### Context keys

| Context key                | Value                        | Description |
|----------------------------|------------------------------|-------------|
| `:bract.ring/ring-handler` | `(fn [request]) -> response` | Ring handler function |


### Config files

The following config resources are provided with the module:
- bract/ring/default.edn  (defaults for Ring wrappers)
- bract/ring/devdelta.edn (defaults for development mode)


### Inducers

All inducers exposed by _bract.ring_ are in the namespace `bract.ring.inducer`. A summary is below:

| Inducer function    | Input context keys         | Output context keys        | Description |
|---------------------|----------------------------|----------------------------|-------------|
| `apply-middlewares` | `:bract.ring/ring-handler` | `:bract.ring/ring-handler` | Apply Ring middlewares |
| `apply-wrappers`    | `:bract.ring/ring-handler` | `:bract.ring/ring-handler` | Apply Ring wrappers |


### Wrappers

_Wrappers_ are functions `(fn [handler context]) -> handler` used to decorate the Ring handler. Wrappers are applied
using the inducer `bract.ring.inducer/apply-wrappers`. The following wrappers are provided:

| Wrapper function                                | Description |
|-------------------------------------------------|-------------|
| `bract.ring.wrapper/uri-prefix-match-wrapper`   | Match URI based on prefix |
| `bract.ring.wrapper/uri-trailing-slash-wrapper` | Easy URI matching by making trailing slash optional |
| `bract.ring.wrapper/traffic-drain-wrapper`      | Respond with HTTP 503 during application shutdown |
| `bract.ring.wrapper/distributed-trace-wrapper`  | Make distributed tracing headers available in request |
| `bract.ring.wrapper/params-normalize-wrapper`   | Normalize params added by `wrap-params` middleware |
| `bract.ring.wrapper/health-check-wrapper`       | Add health-check endpoint - app needs to hook into |
| `bract.ring.wrapper/info-endpoint-wrapper`      | Add /info endpoint to report runtime information |
| `bract.ring.wrapper/ping-endpoint-wrapper`      | Add /ping endpoint that responds with pong |
| `bract.ring.wrapper/unexpected->500-wrapper`    | Turn bad Ring responses and exceptions into HTTP 500 |

Each wrapper may be disabled or enabled based on configuration and they accept several other config parameters.


### Entry points

This module provides entry points for development purpose.

To integrate with [lein-ring](https://github.com/weavejester/lein-ring) put the following in your `project.clj`:

```clojure
:plugins [[lein-ring "0.12.3"]]
:ring {:port    3000                      ; <- optional
       :nrepl   {:start? true :port 3001} ; <- optional
       :handler bract.ring.dev/handler
       :init    bract.ring.dev/init!}
```


<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
