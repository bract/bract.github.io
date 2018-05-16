---
layout: default
title: Module bract.cli - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | [About](/about.html) | [Documentation](/documentation.html) | [Discuss](/discuss.html)

## Module: bract.cli

Clojars coordinates: `[bract/bract.cli "0.6.0-0.1.0"]`


### Context keys

| Context key                   | Value         | Description |
|-------------------------------|---------------|-------------|
| `:bract.cli/config-required?` | Boolean       | Is config file required to be specified? |
| `:bract.cli/command`          | String        | CLI command to execute |
| `:bract.cli/cmd-args`         | String vector | CLI command arguments  |
| `:bract.cli/app-commands`     | Command map   | Commands, e.g. `{"run" {:doc "Run app" :handler myapp.core/run}}` |
| `:bract.cli/pre-inducers`     | Inducer list  | Inducers to run before parsing CLI args |


### Inducers

All inducers exposed by _bract.cli_ are in the namespace `bract.cli.inducer`. A summary is below:

| Inducer function  | Input context keys        | Output context keys        | Description |
|-------------------|---------------------------|----------------------------|-------------|
| `merge-commands`  | `:bract.cli/app-commands` | `:bract.cli/app-commands`  | Add app commands|
| `parse-args`      | `:bract.cli/cli-args`     | `:bract.core/verbose?`     | Parse CLI args  |
|                   |                           | `:bract.core/config-files` |                 |
|                   |                           | `:bract.cli/command`       |                 |
|                   |                           | `:bract.cli/cmd-args`      |                 |
| `execute-command` | `:bract.cli/command`      | depends on the command     | Execute command |
|                   | `:bract.cli/cmd-args`     |                            |                 |
|                   | `:bract.cli/app-commands` |                            |                 |


### Entry points

This module provides the following entry points for CLI integration.


#### Provided Java `main()` method

The namespace `bract.cli.main` is generated as a Java class, hence the function `bract.cli.main/-main` can serve as a
Java `main()` method.

Leiningen users can put the following in `project.clj` under the uberjar profile to use this entry point:

```clojure
:profiles {:uberjar {:aot [bract.cli.main]
                     :main ^:skip-aot bract.cli.main}}
```

After updating `project.clj` as mentioned above , the `lein uberjar` command would produce a standalone JAR file that
you may execute using the command `java -jar <appname>-<version>-standalone.jar` - it invokes the main method.


#### Application's own `main()` method

When you want to customize the initial context or you want to extend the CLI commands supported by the application,
you would want to call the `bract.cli.main/trigger` function with context as the argument. For example, if you want to
support an additional command "status" you could write a namespace as follows:


```clojure
(ns myapp.main
  (:require
    [bract.cli.config :as cli-config]
    [bract.cli.main   :as cli-main])
  (:gen-class))

(defn find-status [context]
  ...)

(defn -main [& args]
  (cli-main/trigger {:bract.core/cli-args    args
                     :bract.cli/app-commands (assoc cli-config/default-commands
                                               "status" {:doc "Find status of XYZ"
                                                         :handler find-status})}))
```
  
You can replace the namespace `bract.cli.main` with `myapp.main` in the steps listed in the sub-section above and it
would all work using the new entry point.


<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
