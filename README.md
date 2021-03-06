# grunt-nw-gyp

[![Node Package](http://img.shields.io/npm/v/grunt-nw-gyp.svg)](https://www.npmjs.org/package/grunt-nw-gyp)
[![Linux Build Status](http://img.shields.io/travis/MiniGod/grunt-nw-gyp/develop.svg)](https://travis-ci.org/MiniGod/grunt-nw-gyp)
[![Windows Build Status](http://img.shields.io/appveyor/ci/MiniGod/grunt-nw-gyp.svg)](https://ci.appveyor.com/project/MiniGod/grunt-nw-gyp)

> Run nw-gyp commands from Grunt.

## Getting Started

This plugin requires Grunt `~0.4.0`

If you haven’t used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you’re familiar with that process, you may install this plugin with this command:

```shell
$ npm install grunt-nw-gyp --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-nw-gyp');
```

For nw-gyp to work you’ll have to install all necessary build tools for your platform, see [nw-gyp’s README.md](https://github.com/rogerwang/nw-gyp#installation) for that matter. However, you do not have to install nw-gyp globally as it is already included with grunt-nw-gyp.

## The “gyp” task

### Overview

In your project’s Gruntfile, add a section named `gyp` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  gyp: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    }
  }
})
```

### Options

#### command

Type: `String`
Default value: `rebuild`

Specify nw-gyp command to execute.

Supported values are `configure`, `build`, `clean` and `rebuild`. See [nw-gyp’s README.md](https://github.com/rogerwang/nw-gyp#commands) for command descriptions.

#### options.debug

Type: `Boolean`
Default value: `false`

Create a debug build.

#### options.arch

Type: `String`
Default value: Your processor’s architecture

Set the target architecture: `ia32`, `x64` or `arm`.

### Usage Examples

#### Default Options

This would be equivalent to `nw-gyp rebuild`.

```shell
$ grunt gyp:addon
```

```js
grunt.initConfig({
  gyp: {
    addon: {}
  }
})
```

#### Configure a debug build

This would be equivalent to `nw-gyp configure --debug`.

```shell
$ grunt gyp:customTarget
```

```js
grunt.initConfig({
  gyp: {
    customTarget: {
      command: 'configure',
      options: {
        debug: true
      }
    }
  }
})
```

#### Build an ARM build

This would be equivalent to `nw-gyp build --arch=arm`.

```shell
$ grunt gyp:arm
```

```js
grunt.initConfig({
  gyp: {
    arm: {
      command: 'build',
      options: {
        arch: 'arm'
      }
    }
  }
})
```

## Running tests

First, install all dependencies:

```shell
$ npm install
```

Then run the tests:

```shell
$ grunt test
```

Testing might take a while as compiling takes time. You may need to install the node development header files before by executing:

```shell
$ ./node_modules/.bin/nw-gyp install
```

## Release History

- v0.5.0 (2014-12-02): Add [`arch` option](https://github.com/MiniGod/grunt-nw-gyp#optionsarch)
- v0.4.1 (2014-08-25): Fix rebuild not stopping execution if one of the commands has failed
- v0.4.0 (2014-07-01): Update `nw-gyp` to `v1.x`
- v0.3.0 (2014-03-05): Update `nw-gyp` to `v0.13.x`
- v0.2.1 (2014-02-21): Hotfix because v0.2.0 didn’t include the main task file `gyp.js`
- v0.2.0 (2013-11-21): Update `nw-gyp` to `v0.12.x`
- v0.1.0 (2013-08-25): Initial release

## License

`grunt-nw-gyp` is licensed under the BSD 2-clause license. See [LICENSE](./LICENSE) for the full license.
