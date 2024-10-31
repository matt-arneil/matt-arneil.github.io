---
layout: post
title:  "Creating a Personal Reusable Framework for Unity"
categories: Games
---

[![Example Game Service Locator Prefab]({{site.url}}//assets/img/serviceLocatorPrefabExample.jpeg)]({{site.url}}/games/2000/01/03/reusable-unity-framework.html)

### Efficiency and Scope
To save time on new projects, I built a personal framework that’s my ‘grab-and-go’ toolkit for Unity. It has a variety of utilities for things like a service locator, application management, scene management, and event messaging. Basically, the things I don’t want to recreate every time and are general enough to be used in most projects.

One of the most valuable tools in my personal game development workflow has been the reusable Unity framework I created, which I have designed to be a starting point for any new small scoped project. The goal behind this framework was to streamline the initial stages of development by providing a simple library of pre-built utilities and tools.

Rather than using a bootstrap scene I opted to have the framework run before any scenes load using **RuntimeInitializeOnLoadMethod**. This removes the need to track and wait on certain scenes to load, as the service locator that this framework is based around will have already loaded by the time any game logic begins.

### Inversion of Control
I've opted for a Service Locator over using a Dependency Injection framework such as VContainer mostly for simplicity's sake. If I'm intentionally limiting the scope of a project and it reaches the point where a DI framework would help then I've probably overcomplicated things. The aim here is to allow for rapid iteration so the service locator I've made is easy to use and set up. Running newly created services at start up is as simple as adding a new prefab nested under the main services prefab. The limited scope intended for this framework also means that there's not a sizeable number of dependencies to manage, so the benefits of using a DI framework probably wouldn't outweight the set up and boilerplate overhead. For further simplicity, the Service Locator intentionally works with MonoBehaviours rather around them as DI frameworks usually need to. With all this said, while a Service Locator can be advantageous for smaller projects, DI frameworks generally scale better in larger, more complex games thanks to their improved testability and modularity so I'm not opposed to using them when needed. It's just worth considering which tools you need and when.

The framework loads a preconfigured hierarchy of prefabs that contain the services needed in the game. Using a nested prefab for this is flexible as it's possible to quickly and visually setup and switch out which services are loaded and in which order they start. Another benefit is the ability to easily customise and switch between platform specific services, such as managing save files on iOS or PC.

The real services used within a game are MonoBehaviours that implement the interface **IService**. However, for testing purposes a dummy service can instead only implement **IService**, avoiding MonoBehaviours which can be an issue in unit testing.
while Service Locator can be advantageous for small projects, DI generally scales better in larger, more complex applications due to its testability and modularity.
