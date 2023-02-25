Hilt provides a standard way to incorporate Dagger dependency injection into an Android application.

_The goals of Hilt are:_

-   To simplify Dagger-related infrastructure for Android apps.
-   To create a standard set of components and scopes to ease setup, readability/understanding, and code sharing between apps.
-   To provide an easy way to provision different bindings to various build types (e.g. testing, debug, or release).

## Hilt Design Overview

Hilt works by code generating your Dagger setup code for you. This takes away most of the boilerplate of using Dagger and really just leaves the aspects of defining how to create objects and where to inject them. Hilt will generate the Dagger components and the code to automatically inject your Android classes (like activities and fragments) for you.