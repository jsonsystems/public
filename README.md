# Welcome to JSONschema.net

[![Hex.pm](https://img.shields.io/hexpm/l/plug.svg)]()

- [Welcome to JSONschema.net](#welcome-to-jsonschemanet)
- [JSON Systems](#json-systems)
- [Web App](#web-app)
- [API](#api)
- [CLI](#cli)
- [What is the goal?](#what-is-the-goal)
- [Who uses this software?](#who-uses-this-software)
- [How can your organization benefit?](#how-can-your-organization-benefit)
- [Specifications](#specifications)
- [FAQs](#faqs)
  - [Web app](#web-app-1)
    - [JSONschema.net looks differen. What changed?](#jsonschemanet-looks-differen-what-changed)
    - [Will my login still work?](#will-my-login-still-work)
    - [Where did my old schemas go?](#where-did-my-old-schemas-go)
  - [CLI](#cli-1)
  - [API](#api-1)
- [About](#about)
- [Contact](#contact)
- [Cookie Policy](#cookie-policy)
- [Privacy Policy](#privacy-policy)

# JSON Systems
JSON Systems provide 3 ways to generate JSON Schema from JSON

1. Web application
2. Application Programming Interface (API)
3. Command Line Interface (CLI)

# Web App
[JSONschema.net](https://www.jsonschema.net) is a modern web application for generating JSON Schema from JSON.
JSON Schema is generated according to
the [JSON Schema Validation: A Vocabulary for Structural Validation of JSON](http://json-schema.org/latest/json-schema-validation.html). 
A number of features make generating schemas quick and easy

- Inbuilt JSON Schema editor with keyword search
- Syntax highlighting, formatting, and code folding
- Highly customisable settings to control how schemas are generated
- JSON Schema keyword autocompletion (according to the specification)

If you've found a bug or have a feature request, please [open a new issue](https://github.com/jsonsystems/public/issues).

# API
The same API that powers [JSONSchema.Net](https://www.jsonschema.net)  is available to developers to automate JSON
schema generation The API is available as both a [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
API and [gRPC](https://grpc.io/) API. If you would like to know more please email help@jsonschema.net.

# CLI
The `jsn` application is a modern CLI for generating JSON Schema from JSON and is available for Mac OS, Windows,
and Linux. If you would like to know more please email help@jsonschema.net. Below is the command-line help output of the
JSON Schema CLI and should give you a feel its functionality.

```shell
The jsn generate-schema command.

To get started you need only provide the path to your JSON document.

Example:

        $ jsn generate-schema example.json

To control which keywords appear in the JSON Schema, use the --keywords flag.

Example:

        $ jsn generate-schema example.json --keywords="additionalItems,additionalProperties,type"

If specified in the --keywords flag, the value of individual keywords can be controlled using keyword specific flags.

Example:

        $ jsn generate-schema example.json --keywords="properties,additionalProperties" --additional-properties=false

As an alternative to parameters, a configuration file can be used to control the resulting schema.

Example:

        $ jsn generate-schema example.json --config=config.yaml

The configuration file can be overwritten using command line flags.

Example:

        $ jsn generate-schema example.json --config=config.yaml --no-pretty=false

Usage:
  jsn generate-schema JSON_FILE [flags]

Examples:
  jsn generate-schema example.json 
  jsn generate-schema example.json --no-pretty=false
  jsn generate-schema example.json --keywords="additionalItems,additionalProperties,type"
  jsn generate-schema example.json --config=config.yaml
  jsn generate-schema example.json --config=config.yaml --no-pretty=true

Flags:
      --additional-items        The "additionalItems" keyword value (default true)
      --additional-properties   The "additionalProperties" keyword value (default true)
      --array-rule string       The rule to use for the "items" keyword (default "type"). Can be one of "empty", "first", "tuple" or "type"
                                 - "empty", use empty schema "{}"
                                 - "first", use the first element only to generate
                                 - "tuple", use all elements in the array
                                 - "type", generate a schema for each type
                                  
      --base-uri string         Defines a URI for the schema and the value of the "$id" keyword (default "https://example.com/root.json")
  -c, --config string           Config file path
      --examples-rule string    The rule to use for generation of "examples" keyword (default "full"). Can be one of "primitive", "compound" or "full"
                                 - "primitive", only generate examples for string, number, boolean, null 
                                 - "compound", only generate examples for objects and arrays
                                 - "full", generate examples for all types
                                 
  -h, --help                    help for generate-schema
      --js-types-only           Use "number" for all numeric types in "type" key
      --keywords strings        A comma separated list of keywords to be generated. Must not contain spaces. Available values
                                 - "additionalItems"
                                 - "additionalProperties"
                                 - "default"
                                 - "description"
                                 - "examples"
                                 - "id"
                                 - "items"
                                 - "minimum"
                                 - "properties"
                                 - "required"
                                 - "schema"
                                 - "title"
                                 - "type"
                                 - "uniqueItems"
                                
                                Consider using the "config" flag to manage keywords (default [schema,id,type,properties,items])
  -p, --no-pretty               Do not pretty print the output
      --specification string    The JSON Schema specification to use (default "201909"). Can be one of "draft04", "draft06", "draft07" or "201909"
                                 - "draft04" use the Draft 4 JSON Schema specification
                                 - "draft06" use the Draft 6 JSON Schema specification
                                 - "draft07" use the Draft 7 JSON Schema specification
                                 - "201909" use the Draft 2019-09 JSON Schema specification
                                 
      --unique-items            The "uniqueItems" keyword value (default false)

Global Flags:
  -f, --logs-format string   Specify logs format: "plain" or "json" (default "plain")
  -x, --trace                Trace output (very noisy logs up to trace level) not usable in normal situations
  -v, --verbose              Verbose output (up to debug level)
```


# What is the goal?
JSON Schema is great, but can be verbose. For example, a single empty JSON object, `{}`, can be described by:

```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "additionalProperties": true,
  "definitions": {},
  "id": "http://example.com/example.json",
  "properties": {
    "description": "This accepts anything, as long as it's valid JSON.",
    "title": "Empty Object"
  },
  "type": [
    "object",
    "null"
  ]
}
```

Even schemas for small APIs can quickly become hundreds of lines long. Writing schemas by hand is tedious and time consuming, and often impractical. JSONSchema.Net makes schema generation quick and painless.

# Who uses this software?
Anyone wishing to generate JSON schema from JSON. Typical users are web developers and mobile app developers.
Some educational institutions also use [JSONSchema.Net](https://www.jsonschema.net) to teach JSON Schema and the core
options defined by [JSON Schema Validation](http://json-schema.org/latest/json-schema-validation.html).

# How can your organization benefit?
The web app, CLI, and API, can save you and anyone on your team a lot of time.
If your software uses JSON, it's good practice to validate any (JSON) data it receives, against a schema.
A CLI and API are aimed for teams wishing to integrate JSON Schema with their software or processes.

# Specifications
JSON Schema specificaiton is split into three parts

1.  Core - The basic foundation of JSON Schema.
2.  Validation - The validation keywords of JSON Schema.
3.  Hyper-Schema - The hyper-media keywords of JSON Schema.

JSONSchema.Net follows the Validation part of the overall specification. [json-schema.org/specification.html](http://json-schema.org/specification.html) is a good place to learning more.

Versioning of JSON Schema specifications can be confusing. [json-schema.org](http://json-schema.org) maintains a helpful list of [specification-links](http://json-schema.org/specification-links.html). In reverse chronological order:

- Latest Snapshot (work in progress)
- Draft 7
- Draft 6
- Draft 5
- Draft 4
- Draft 3
- Drafts 0/1/2

Each version updates (to varying degrees) the three parts of JSON Schema specification: Core, Validation, and Hyper-Schema.

# FAQs
## Web app
### JSONschema.net looks differen. What changed?
In January 2022, a new version of the JSON Schema web app was launched. This new version was a complete rewrite of the 
web app and brought with it many new features and bug fixes.

### Will my login still work?
Yes, accounts and account details were not impacted by the launch of the new version

### Where did my old schemas go?
JSONschema.net recently underwent a 

## CLI
TODO

## API
TODO

# About
Created by Jack Wootton, Mateusz Kyc, and Kevin Glenny.
Copyright 2017. Apache Licensed.

# Contact
- Email: help@jsonschema.net
- 
# Cookie Policy
Our cookie policy can be read at [cookies.md](https://github.com/jsonsystems/json-schema/blob/master/cookies.md)

# Privacy Policy
Our privacy policy can be read at [privacy.md](https://github.com/jsonsystems/json-schema/blob/master/privacy.md)