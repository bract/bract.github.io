---
layout: default
title: Bract Home - Multi-purpose, modular application initialization framework for Clojure
---
# Home | [About](/about.html) | [Documentation](/documentation.html) | [Discuss](/discuss.html)


_**Bract requires Clojure 1.7 or higher, Java 7 or higher.**_

_**Gossamer requires Clojure 1.8 or higher.**_


## Latest release

|---------------------------------------------------------|-------------------------------------------------|---------------------------------------|---------------------------------------------------------------|
| Module                                                  | Description                                     | Clojars artifact                      | Dependencies                                                  |
|---------------------------------------------------------|-------------------------------------------------|---------------------------------------|---------------------------------------------------------------|
| [bract.core](https://github.com/bract/bract.core)       | Core functionality                              | `[bract/bract.core    "0.6.2"]`       | [Keypin](https://github.com/kumarshantanu/keypin) for config  |
| [bract.cli](https://github.com/bract/bract.cli)         | CLI support                                     | `[bract/bract.cli     "0.6.2-0.1.1"]` | [tools.cli](https://github.com/clojure/tools.cli)             |
| [bract.dev](https://github.com/bract/bract.dev)         | REPL support                                    | `[bract/bract.dev     "0.6.2-0.2.0"]` | [tools.namespace](https://github.com/clojure/tools.namespace) |
| [bract.ring](https://github.com/bract/bract.ring)       | [Ring](https://github.com/ring-clojure) support | `[bract/bract.ring    "0.6.2-0.2.0"]` |                                                               |
| [gossamer.core](https://github.com/bract/gossamer.core) | Micro Web framework                             | `[bract/gossamer.core "0.6.2-0.3.0"]` | [Calfpath](https://github.com/kumarshantanu/calfpath) (routing), [Cambium](https://github.com/cambium-clojure) (logging) |


## Quick start - Bare bones application

To generate a bare bones Bract application, run the following command:

```shell
$ lein new bract myapp
$ cd myapp
```

Follow the generate code and `README.md` file for further steps.

## Quick start - Web service or application

To generate a server-side web application combining several Bract modules, run the following command:

```shell
$ lein new gossamer myapp
$ cd myapp
```

Once you generate the application, you can use the following commands:

```shell
$ lein repl                  # load application in the REPL - run (help) to see help
$ lein ring server-headless  # start application in DEV mode
$ lein do clean, uberjar     # generate uberjar to run in standalone mode
$ java -jar target/uberjar/myapp-0.1.0-SNAPSHOT-standalone.jar -vf config/config.edn
```

Follow the generated code and `README.md` file for details.

## License

Copyright © 2017-2021 [Shantanu Kumar](https://github.com/kumarshantanu)

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.

<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
