---
layout: default
title: About Bract - Multi-purpose, modular application initialization framework for Clojure
---
# [Home](/) | About | [Documentation](/documentation.html) | [Discuss](/discuss.html)

## Rationale

Application configuration and initialization are tangential to delivering business value, yet we frequently get bogged
down by their incidental complexity. Application development could be a wonderful experience if we only have to focus
on the application logic without worrying about configuration, initialization and the sundry development/maintenance
tasks that applications frequently need. This should be a solved problem in a repeatable, predictable manner.


### What is Bract?

Bract is a Clojure framework to bring power and flexibility to application configuration and initialization workflow.

Bract aims to:

- Bind the following pieces together
  - Application entry-point
  - Application configuration
  - Steps to initialize and launch application
- Allow extensions to Bract facilities (e.g. any library/framework integration) via modules

Bract does not aim to:

- Prescribe which environments (Dev/QA/Prod etc.) you may have
- Decide which libraries you should use (except [Keypin](https://github.com/kumarshantanu/keypin) for configuration)
- Make you use dependency injection, let alone any particular DI library
- Discourage you from using dependency injection


Bract is made of _bract.core_ (with [Keypin](https://github.com/kumarshantanu/keypin) as the only dependency for config
support) and a bunch of modules for various purposes. While _bract.core_ is low level and prescribes no style, it is
possible to author opinionated Bract modules on top of it. One may even extend Bract to build a custom application
framework. Bract is suited for various types of applications, e.g. command-line tools, web services, batch jobs, web
applications etc. and integrates well with tangential, yet relevant aspects such as configurable JVM logging.


### How it works

The _bract.core_ module is the minimum requirement for using Bract, and is used by all other modules. The essential
idea behind Bract is the "inducer function" `(fn [context & args]) -> context`, also called _inducer_. One or more
(often nested) inducers form the initialization workflow. The `context` is a map passed to one inducer after another.

#### Inducer

An inducer's role is to bring about a certain kind of change. An inducer receives the context map as argument, and must
always return either updated or unchanged context. Say for example, a `config-reader` inducer may discover the config
file name from the context and populate the context with loaded config before returning. An inducer usually does not
know which other inducers are participating in the workflow. The inducers and their order of invocation are generally
decided by either a Bract module (as entry point) or by the application developers. Various inducers are provided by
the Bract modules and by the application developers.

#### Well known keys

An inducer generally needs information to do its job, which it can find in the context and in the optional arguments.
The information an inducer finds in the context is usually put in by other inducers that executed earlier. However,
inducers only have hard dependency on well-known context (or config) keys. This helps to keep inducers decoupled from
each other while encouraging flexible workflows.

#### Entry point

The top level inducer workflow is usually executed from either a `-main` or an implicitly called function. An
application may very well choose to do its own processing before invoking Bract initialization, but generally Bract
modules make the job easier by providing such entry-point functions.

<a href='https://github.com/bract'><img style='position: absolute; top: 0; right: 0; border: 0;' src='https://camo.githubusercontent.com/652c5b9acfaddf3a9c326fa6bde407b87f7be0f4/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67' alt='Fork me on GitHub' data-canonical-src='https://s3.amazonaws.com/github/ribbons/forkme_right_orange_ff7600.png'></a>
