---
description: A utility to manage and integrate SPEQ-based workflows
---

# Speqqy

Speqqy is a TypeScript-based utility with plans to support:

* Generation of a scaffold
* Compilation
* Linting
* Rules Validation
* Documentation Generation
* Definition Conversion \(e.g. OpenAPI -&gt; SPEQ\)

{% hint style="warning" %}
Speqqy is currently in draft development. Features will likely be incomplete or missing.  
  
Use at your own risk.
{% endhint %}

## Installation

`npm install speqqy`

## Commands

`speqqy <command>`

| Command | Description |
| :--- | :--- |
| `speqqy -h --help` | Output usage information |
| `speqqy -g --generate` | Generate a `.speq` scaffold to get started |
| `speqqy -c --compile` | Resolve all imports and generate `.def.speq` definitions |
| `speqqy -l --lint` | Lint / validate a SPEQ file |
| `speeqy -v --version` | Display current version of `speqqy` |

## Usage

Refer to `npm` or execute `speqqy -h` for detailed usage instructions.



