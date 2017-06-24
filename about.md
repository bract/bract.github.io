---
layout: default
title: About Bract - Multi-purpose, modular application initialization framework for Clojure
---

# [Home](/index.html)    |    About    |    [Documentation](/documentation.html)    |    [Discuss](/discuss.html)

## Rationale

Application configuration and initialization are tangential to delivering business value, yet we frequently get bogged
down by their incidental complexity. Application development could be a wonderful experience if we only have to focus
on the application logic without worrying about configuration, initialization and the sundry development/maintenance
tasks that applications frequently need. This should be a solved problem in a repeatable, predictable manner.


### What is Bract?

Bract is a Clojure framework to bring power and flexibility to application configuration and initialization workflow.

Bract aims to bind the following pieces together:

- Application entry-point
- Application configuration
- Steps to initialize and launch application
- Extensions via Bract modules
- Integration with libraries/frameworks via Bract modules

Bract does not aim to:

- Prescribe what environments (Dev/QA/Prod etc.) you may have
- Decide which libraries you should use (except Keypin for configuration)
- Make you use dependency injection, let alone any particular DI library
- Discourage you from using dependency injection


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

#### Entrypoint

The top level inducer workflow is usually executed from either a `-main` or an implicitly called function. An
application may very well choose to do its own processing before invoking Bract initialization, but generally Bract
modules make the job easier by providing such entrypoint functions.
