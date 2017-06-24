---
layout: default
title: Bract Documentation - Multi-purpose, modular application initialization framework for Clojure
---

# [Home](/index.html)    |    [About](/about.html)    |    Documentation    |    [Discuss](/discuss.html)

Bract [revolves around](/about.html#how-it-works) the idea of _inducers_. Here we will talk about working with inducers and other related aspects.

## Quickstart

Bract covers disparate aspects of application initialization, so let us take a contrived example.

TODO

## Concepts

TODO

## Demo applications

There are few demo applications that may be useful to understand how Bract may be used.

* **[Wordcount](https://github.com/bract/bract.demo.wordcount)** is a simple CLI application that reads STDIN and prints the word count
  * Configuration: Stop words (stop words are excluded from the word count)
  * CLI entry point for running application as uberjar
  * Unit tests entry point
  * REPL-based development entry point
* **[Diceroll](https://github.com/bract/bract.demo.diceroll)** is a simple Ring based web application that responds with a roll of dice
  * Dice configuration
  * CLI entry point for running application as uberjar
  * Web development entry point usig [lein-ring](https://github.com/weavejester/lein-ring)
  * Unit tests entry point
  * REPL-based development entry point
  * Configurable Ring middleware using wrapper inducers
* **[TodoMVC](https://github.com/bract/demo.todomvc)** is an interactive TodoMVC web application developed using Ring and ClojureScript
  * Database configuration
  * Database migration entry point
  * CLI entry point for running application as uberjar
  * Unit tests entry point
  * REPL-based development entry point
  * ClojureScript


## Howto

TODO
