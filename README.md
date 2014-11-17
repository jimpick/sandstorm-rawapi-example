# Sandstorm Raw API Example App

This is an example [Sandstorm](https://sandstorm.io) application which uses the raw [Cap'n Proto](https://capnproto.org)-based Sandstorm API to serve a web UI without an HTTP server. Most apps instead use `sandstorm-http-bridge` wrapping a traditional server, but this one does't.

## Why do that?

You might want to write a Sandstorm app using the raw API if:

* You want to be as efficient as possible. Raw API apps -- especially if written in C++ or Rust -- take drastically less RAM and start much faster.
* You want to avoid legacy cruft. A traditional HTTP server is a huge, complicated piece of code much of which is not important for Sandstorm.
* You want to use a language that has poor HTTP support, but good Cap'n Proto RPC support, such as C++ or Rust.

That said, you should prefer `sandstorm-http-bridge` around a traditional HTTP server if:

* You are porting an existing HTTP-based app.
* You want to build on top of a standard HTTP server framework.
* You want to use a programming language that doesn't have good Cap'n Proto RPC support.

## Instructions

1. Get a Linux machine.
2. Install the Clang C++ compiler version 3.4 or later.
3. Install [Cap'n Proto](https://capnproto.org) 0.5.0 or newer. (As of this writing, 0.5.0 isn't out yet; install the latest code from git.)
4. Install [Sandstorm](https://github.com/sandstorm-io/sandstorm) and make sure it is successfully running locally.
5. Clone this git repo.
6. CD to the repo and `make dev`.
7. Open your local Sandstorm. The app should be visible there.
8. Ctrl+C in the terminal running `make dev` to disconnect.

## Building your own

You can use this code as a starting point for your own app.

1. Edit `sandstorm-pkgdef.capnp`, read the comments, and edit. At the very least you want to rename the app and set a new App ID.
2. Place your own client code (HTML, CSS, Javascript, etc.) in the `client` directory.
3. Have your client code use HTTP GET, PUT, and DELETE requests to store user data under the HTTP path `/var`. You can create files under `/var` with any name, but you cannot create sub-directories (for now).
4. Use `make dev` to test.
5. Type just `make` to build a distributable package `package.spk`.

## Questions?

[Ask on the dev group.](https://groups.google.com/group/sandstorm-dev)
