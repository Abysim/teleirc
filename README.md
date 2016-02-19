![Logo](/logo.png)

A simple [Telegram](https://telegram.org/) ↔ IRC gateway.

[Changelog](https://fruitiex.org/blog/tag/teleirc/)

#### Features:

* Supports multiple IRC channel ↔ Telegram group pairs
* Telegram messages are always relayed to their respective IRC channel
* IRC messages can be configured either to be relayed always, or only
  when the bot is hilighted via a configurable regexp
* Supports Telegram media files, URL to file sent to IRC

Quick start
-----------

Make sure you've installed Node.js.

1. Install the teleirc npm module with `npm install -g teleirc` (might need sudo)
2. Generate a default config using `teleirc --genconfig`
3. Set up your bot with [BotFather](https://telegram.me/botfather)
4. Use the `/setprivacy` command with `BotFather` to allow the bot to
   see all Telegram messages
5. Edit the default config `$EDITOR ~/.teleirc/config.js`
6. Run `teleirc`
7. Invite your bot to any Telegram groups you've configured it for
8. Greet your bot once on each of your Telegram groups :tada:! This is needed
   to fetch (and store!) an internally used group ID, making communication
   from IRC to the correct Telegram group possible.

Optional:

- For your convenience, there is an included systemd unit file in
  `teleirc.service`.
- You can change your Telegram Bot's profile picture with the `/setuserpic`
  BotFather command. [Here's](/icon.png) an example icon for you.
- You can tell Telegram which commands the teleirc bot supports by using the
  `/setcommands` BotFather command. You may copy-paste the contents of
  [`commands.txt`](/commands.txt) to show all supported commands to Telegram
  clients.

Developer install (from git)
----------------------------

    git clone https://github.com/FruitieX/teleirc
    cd teleirc
    npm install

Then follow the instructions under `Setup`, with the exception of step 1.
Also, instead of using the `teleirc` command, use `node teleirc.js` inside the repo.

Use the [`develop`](https://github.com/FruitieX/teleirc/tree/develop) branch for developing, and please also send any pull requests to this branch. The [`master`](https://github.com/FruitieX/teleirc/tree/master) branch contains the latest stable version which is also released on [npm](https://www.npmjs.com/package/teleirc).

Make sure that the unit tests pass before submitting your pull request, using `npm test`.

# [node-dwebp-bin](https://www.npmjs.org/package/dwebp-bin)

[![Build Status](https://travis-ci.org/1000ch/node-dwebp-bin.svg?branch=master)](https://travis-ci.org/1000ch/node-dwebp-bin)
[![NPM version](https://badge.fury.io/js/dwebp-bin.svg)](http://badge.fury.io/js/dwebp-bin)
[![Dependency Status](https://david-dm.org/Abysim/node-dwebp-bin.svg)](https://david-dm.org/Abysim/node-dwebp-bin)
[![devDependency Status](https://david-dm.org/Abysim/node-dwebp-bin/dev-status.svg)](https://david-dm.org/Abysim/node-dwebp-bin#info=devDependencies)

## Dependencies on Linux

WebP requires following libraries on Linux. See [detail](https://developers.google.com/speed/webp/docs/compiling#compiling_on_unix-like_platforms).

```sh
$ sudo apt-get install libjpeg-dev libpng-dev libtiff-dev libgif-dev
```

## Install

```sh
$ npm install --save dwebp-bin
```

## Usage

### Command Line

```sh
$ dwebp input.webp -o output.png
```

### From source file

```js
var execFile = require('child_process').execFile;
var dwebp = require('dwebp-bin').path;

execFile(dwebp, ['input.webp', '-o', 'output.png'], function (error) {
  if (error) {
    throw error;
  }

  console.log('Image was converted');
});
```

### Options

```sh
Usage: dwebp in_file [options] [-o out_file]

Decodes the WebP image file to PNG format [Default]
Use following options to convert into alternate image formats:
  -pam ......... save the raw RGBA samples as a color PAM
  -ppm ......... save the raw RGB samples as a color PPM
  -bmp ......... save as uncompressed BMP format
  -tiff ........ save as uncompressed TIFF format
  -pgm ......... save the raw YUV samples as a grayscale PGM
                 file with IMC4 layout
  -yuv ......... save the raw YUV samples in flat layout

 Other options are:
  -version  .... print version number and exit
  -nofancy ..... don't use the fancy YUV420 upscaler
  -nofilter .... disable in-loop filtering
  -nodither .... disable dithering
  -dither <d> .. dithering strength (in 0..100)
  -mt .......... use multi-threading
  -crop <x> <y> <w> <h> ... crop output with the given rectangle
  -scale <w> <h> .......... scale the output (*after* any cropping)
  -flip ........ flip the output vertically
  -alpha ....... only save the alpha plane
  -incremental . use incremental decoding (useful for tests)
  -h     ....... this help message
  -v     ....... verbose (e.g. print encoding/decoding times)
  -noasm ....... disable all assembly optimizations
```

## License

This is licensed under BSD.

WebP is licensed under [Creative Commons Attribution 3.0 License](http://creativecommons.org/licenses/by/3.0/).

