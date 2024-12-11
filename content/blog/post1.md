+++
title = 'Journal #1: Jam Tools Core'
date = 2024-12-02T14:38:33+02:00
draft = false
type = 'blog'
+++

I'm wanting to have a public journal for my current efforts of software development, so here it is.

Right now I'm focusing on 2 projects:

- Jam Tools - An open-source music performance application
- Music Sniper - An online music collaboration application

This post is about Jam Tools, more specifically about the framework that powers the application, [Springboard](https://docs.jam.tools/springboard/overview) (a full-stack React framework created out of necessity for this application) and [Jam Tools Core](https://docs.jam.tools/jamtools/overview) (additional code to make it easy to work with MIDI and IO devices).

Jam Tools is a realtime music communication tool that allows musicians to communicate thoughts to each other while playing music. It's meant to be used with everyone in the same room, and ideas can be circulated among different phones and screens in the room. The goal is to communicate lyrics, chord progressions, and messages such as "slow down" or "let's play something funky". It also helps automate [MIDI](https://en.wikipedia.org/wiki/MIDI)-related processes and control [WLED](https://kno.wled.ge) lighting.

One thing the application requires is using a phone/tablet to remotely control something on a separate computer that has the MIDI devices plugged in. From experience of trying to build this program a few times, in order for this to scale this means there needs to be high cohesion between the UI code running on the phone, and the feature-level code related to MIDI functionality running on the server. Another required feature is the application to optionally run standalone in the browser. Given these constraints, the application needs to run in multiple different deployment contexts, such as:

- Browser local/offline
- Browser with server

There is also active development to support the following:

- Mobile app local/offline
- Mobile app with server
- Desktop app local/offline
- Desktop app with remote server
- Desktop app as server

Because of these requirements, the project has since turned into a framework for creating cross-platform applications, with an emphasis on isomorphic TypeScript code, which helps with the cohesion of UI and MIDI-related code.

The generic application framework powering the application is available on npm, published as [`springboard`](https://www.npmjs.com/package/springboard), whereas the code to make MIDI-related features is located at [`@jamtools/core`](https://www.npmjs.com/package/@jamtools/core). Check out the [repo](https://github.com/jamtools/jamtools) and [documentation](https://docs.jam.tools) for more info.

I am now using `springboard` for all my current applications in development, whether they are related to music or not. I find the patterns of dependency injection make it easy to write tests for otherwise complex pieces of functionality.

The project is open-source to enable developers to make their own MIDI applications, and also collaborate together on features to include into a common application. Feel free to join the Jam Tools [Discord server](https://jam.tools/discord) to join the conversation.
