---
layout: default
title: Bract#58; Multi-purpose, modular application initialization framework for Clojure
---

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
- Extensions to _bract.core_ via Bract modules
- Integration with libraries/frameworks via Bract modules

Bract does not aim to:

- Prescribe what environments (Dev/QA/Prod etc.) you may have
- Decide which libraries you should use (except Keypin for configuration)
- Make you use dependency injection, let alone any particular DI library
- Discourage you from using dependency injection


## License

Copyright © 2017 Shantanu Kumar (kumar.shantanu@gmail.com, shantanu.kumar@concur.com)

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
