# swagger-merger

[![Greenkeeper badge](https://badges.greenkeeper.io/WindomZ/swagger-merger.svg)](https://greenkeeper.io/)
[![Build Status](https://travis-ci.org/WindomZ/swagger-merger.svg?branch=master)](https://travis-ci.org/WindomZ/swagger-merger)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Dependency](https://david-dm.org/WindomZ/swagger-merger.svg)](https://david-dm.org/WindomZ/swagger-merger)
[![Coverage Status](https://coveralls.io/repos/github/WindomZ/swagger-merger/badge.svg?branch=master)](https://coveralls.io/github/WindomZ/swagger-merger?branch=master)
[![Standard - JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com/)

> Merge **multiple** swagger files into **a** swagger file, support **JSON**/**YAML**.

[![NPM](https://nodei.co/npm/swagger-merger.png)](https://nodei.co/npm/swagger-merger/)

[![swagger-merger](https://img.shields.io/npm/v/swagger-merger.svg)](https://www.npmjs.com/package/swagger-merger)
![status](https://img.shields.io/badge/status-stable-green.svg)

## Features

- [x] Command line interface.
- [x] _Support_ **JSON**/**YAML** swagger files.
- [x] _Merge_ ***multiple*** swagger files into ***a*** swagger file.

## Installation

```bash
npm install -g swagger-merger
```

## Usage

```bash
$ swagger-merger -h

  Usage: swagger-merger [-h] [-v] [-c] [-o file] <-i file | file>

  Merge multiple swagger files into a swagger file, just support JSON/YAML.

  Options:

    -h, --help           output usage information
    -V, --version        output the version number
    -i, --input <file>   input a main/entry JSON/YAML swagger file
    -o, --output <file>  output a merged JSON/YAML swagger file
    -c, --compact        compact JSON/YAML format string
    --debug              debug mode, such as print error tracks
```

### $ref

Include a _single-level_ of swagger file.

For example:
```yaml
parameters:
    - $ref: "./name.yaml"
    - $ref: "./year.yaml"
```

### $ref#*

Include a _multi-level_ of swagger file.

For example:
```yaml
paths:
  $ref#pets: "./paths/pets.yaml"
  $ref#pets-id: "./paths/pets-id.yaml"
definitions:
  $ref#pets: "./definitions/pets.yaml"
  $ref#error: "./definitions/error.yaml"
```

## Examples

Run shell `./example/example.sh` for more help.

### [heroku-pets](https://github.com/WindomZ/swagger-merger/tree/master/example/heroku-pets)

- Official swagger example
- No modification

```bash
$ swagger-merger -i ./example/heroku-pets/index.yaml
$ swagger-merger -i ./example/heroku-pets/index.json
```

### [echo](https://github.com/WindomZ/swagger-merger/tree/master/example/echo)

- Official swagger example
- Modify to support for [$ref](#ref) tags

```bash
$ swagger-merger -i ./example/echo/index.yaml
$ swagger-merger -i ./example/echo/index.json
```

### [petstore_simple](https://github.com/WindomZ/swagger-merger/tree/master/example/petstore_simple)

- Official swagger example
- Modify to support for [$ref#*](#ref-1) tags

```bash
$ swagger-merger -i ./example/petstore_simple/index.yaml
$ swagger-merger -i ./example/petstore_simple/index.json
```

## License

The [MIT License](https://github.com/WindomZ/swagger-merger/blob/master/LICENSE)
