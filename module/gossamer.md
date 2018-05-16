---
layout: default
title: Module gossamer.core - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | [About](/about.html) | [Documentation](/documentation.html) | [Discuss](/discuss.html)

## Module: gossamer.core

Clojars coordinates: `[bract/gossamer.core "0.6.0-0.1.0"]`


### Context keys

| Context key                 | Value          | Description |
|-----------------------------|----------------|-------------|
| `:gossamer/calfpath-routes` | Vector of maps | Vector of Calfpath route maps |
| `:gossamer/route-wrappers`  | Vector of fns  | Vector of route wrapper functions |


### Config files

The following config resources are provided with the module:
- `gossamer/core/config.edn` (defaults for Gossamer)
- `gossamer/core/config.logback.dev.edn` (DEV mode defaults for Logback)
- `gossamer/core/config.logback.edn` (defaults for Logback)


### Inducers

All inducers exposed by _bract.ring_ are in the namespace `bract.ring.inducer`. A summary is below:

| Inducer function                | Input context keys | Output context keys        | Description |
|---------------------------------|--------------------|----------------------------|-------------|
| `log-mdc-codec-init-only`       | FIXME              | FIXME                      | FIXME       |
| `register-logback-deinit`       | FIXME              | FIXME                      | FIXME       |
| `log-mdc-codec-init`            | FIXME              | FIXME                      | FIXME       |
| `calfpath-routes->ring-handler` | FIXME              | FIXME                      | FIXME       |
| `apply-route-wrappers`          | FIXME              | FIXME                      | FIXME       |


### Usage

This module may be easily used using its Leiningen template.

`lein new gossamer <application-name>`

FIXME


<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
