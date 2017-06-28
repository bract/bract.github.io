---
layout: default
title: Bract Documentation - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | [About](/about.html) | Documentation | [Discuss](/discuss.html)

## Keypin

The [Keypin](https://github.com/kumarshantanu/keypin) library is included with the _bract.core_ module. Bract uses
Keypin to read/write config and to define keys that can be looked up in the config. Keypin documentation is out of
scope here, but let us quickly see how to define keys using Keypin that we can use to look up their values.

Require namespaces:

```clojure
(ns demo.app
  (:require
    [keypin.core :as keypin]
    [keypin.util :as kputil]))
```

Key definition:

```clojure
(keypin/defkey
  addr [:addr string?           "IP address"]
  port [:port #(< 1023 % 65535) "port number" {:parser kputil/any->int}])
```

Look up value:

```clojure
(port {:port 1234})  ; returns 1234
(port {:foo "bar"})  ; throws exception because port is missing
```


## Inducer

Bract [revolves around](/about.html#how-it-works) the idea of _inducers_. Let us write a hello-world inducer first:

```clojure
(defn hello-world
  [context]
  (println "Hello World!")
  context)
```

Now let us write an inducer that uses the context:

```clojure
(keypin/defkey
  email-tpl-file [:email-tpl-file string? "Email template filename"]
  email-template [:email-template string? "Email template"])

(defn cache-email-template
  [context]
  (require '[clojure.java.io :as io])
  (let [tpl-file (email-tpl-file context)
        tcontent (slurp)]
    (if-let [tpl-resource (io/resource tpl-file)]
      (assoc context (key email-template) (slurp tpl-resource))
      (throw (ex-info "Missing template file in classpath" {:email-template-file tpl-file})))))
```

Once you have several inducers and want to execute them in order, below is how you can do so:

```clojure
(require '[bract.core.inducer :as bc-inducer])

(bc-inducer/induce {}  ; <- initial context
  [app/foo  ; <- this is an inducer
   app/bar  ; <- this is also an inducer
   app/baz  ; <- and this one too
   ])
```


## Demo applications

There are few simple demo applications that may be useful to understand how Bract can be used.

* **[Wordcount](https://github.com/bract/demo.wordcount)** is a simple CLI application that reads STDIN and prints the word count
  * Configuration: Stop words (stop words are excluded from the word count)
  * CLI entry point for running application as uberjar
  * Unit tests entry point
  * REPL-based development entry point
* **[Diceroll](https://github.com/bract/demo.diceroll)** is a simple Ring based web application that responds with a roll of dice
  * Dice configuration
  * CLI entry point for running application as uberjar
  * Web development entry point usig [lein-ring](https://github.com/weavejester/lein-ring)
  * Unit tests entry point
  * REPL-based development entry point
  * Configurable Ring middleware using wrapper inducers
* **[TodoMVC](https://github.com/bract/demo.todomvc)** is an interactive TodoMVC webapp developed using Ring and ClojureScript
  * Logging as JSON, as text, configuration
  * Database configuration
  * Database migration entry point
  * CLI entry point for running application as uberjar
  * Unit tests entry point
  * REPL-based development entry point
  * ClojureScript


## Modules

Documentation of individual Bract modules is as follows:

* [bract.core](/module/core.html)
* [bract.cli](/module/cli.html)
* [bract.dev](/module/dev.html)
* [bract.ring](/module/ring.html)


## Howto

TODO

<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
