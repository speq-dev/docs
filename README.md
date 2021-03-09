---
description: The 'universal spec' has arrived
---

# Why SPEQ?

**SPEQ** is a definition to describe APIs, services and databases in a **protocol-agnostic** manner. 

That means SPEQ can act as your defacto definition for REST, GraphQL, Kafka, gRPC, SQL and any other service that follows a client-server model within your organization or team.

SPEQ is backed by the [**Speqqy**](https://www.npmjs.com/package/speqqy) ****utility with plans to support: 

* Generation of SPEQ Starter
* Compilation
* Linting
* Rules Validation
* Documentation Generation
* Definition Conversion \(e.g. OpenAPI -&gt; SPEQ\)

What SPEQ gives you over other specifications and schema formats is:

* A consistent format to build tooling against
* 2-way conversion of SPEQ to definitions like OpenAPI, Protobuf, Avro, AsyncAPI
* Auto-generation of change logs / diffs between service deployments
* The ability to set organization-wide governance and rules

{% hint style="warning" %}
SPEQ is currently under active development of its first draft version is subject to frequent changes.   
  
It is recommended to avoid use in production environments.
{% endhint %}

## The Big Picture

### SPEQ Basics

<table>
  <thead>
    <tr>
      <th style="text-align:left">Types</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">File Format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Definition</td>
      <td style="text-align:left">
        <p><b>Required</b>
        </p>
        <p>Describes servers, versions, development stages, governance rules, resources,
          operations and message/metadata schemas for one or more services.</p>
        <p></p>
        <p>Can be split and organized how a team wishes.</p>
      </td>
      <td style="text-align:left"><code>*.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Package</td>
      <td style="text-align:left">
        <p><b>Auto-Generated | Read-Only</b>
        </p>
        <p>When a <code>.def.speq</code> is compiled with <code>speqqy</code>, all references
          are resolved, external schemas and specifications are converted, rules
          will be validated and by default one definition will be generated for each
          service and it&apos;s associated stages and versions, preventing exposure
          of internal services and descriptions.</p>
        <p></p>
        <p>Future support includes custom package</p>
      </td>
      <td style="text-align:left"><code>{service}-{stage}-{version}.pkg.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Change Log</td>
      <td style="text-align:left">
        <p><b>Auto-Generated | Read-Only</b>
        </p>
        <p>An auto-generated list of changes, generated at compile time between the
          previous SPEQ and the current. Useful for generating release notes.</p>
      </td>
      <td style="text-align:left"><code>*.changelog.speq</code>
      </td>
    </tr>
  </tbody>
</table>

### SPEQ Advanced

Once you have your services defined within SPEQ, you may want to start adding examples, creating tests, virtualizing services and more. SPEQ provides a number

|  |  |  |
| :--- | :--- | :--- |
| Payload | Describes a sample payload \(message & metadata\) that conforms to a SPEQ definition. | `*.payload.speq` |
| Tests | Describe one or more service functional, end-to-end or contract tests, referencing SPEQs that can be used by vendors and tooling to automate testing. | `*.tests.speq` |
| Virts | Describe virtualized service configuration, that can be used by vendors and tooling to stand up a virtualized instance of your services. | `*.virts.speq` |
| Props | A collection of freeform data objects that can be referenced in SPEQ tests, virts and scenarios. | `*.props.speq` |
| Protocol | A SPEQ that describes the unique properties of a service or API.   For example:  Should it support client streaming?  What metadata does it support?  Does the API require serialization and deserialization?   A set of default proto SPEQs are defined \(e.g. for REST, GraphQL, gRPC, Kafka\), but custom protocols can be defined at any time, but should be prefixed with `x-` | `*.proto.speq` |

## What about edge cases?

Every API, database and service has unique implementations, but what makes SPEQ unique is that it's built around an architecture that is protocol-agnostic:

![agnostic-architecture](https://i.imgur.com/JVYo97T.png)

With this base implementation, the key metadata documenting the API is consistent and rules can be put in place for protocol-specific logic or even organization-specific logic with custom extensions.

## What about other definitions?

We consider there to be three classifications of definitions. These are not 'hard and fast' rules, but general guidelines to help frame the current ecosystem of service definitions.

### Authoritative

These are almost never out-of-date due to the fact that they drive the operation of the service itself, due to either serialization/deserialization logic or due to the fact that the server itself requires knowledge of the definition to operate.

* GraphQL Schema
* Protobuf
* Apache Avro

### Semi-Authoritative

* SQL DDL
* Parquet

### Non-Authoritative

These may often be out of date due to the fact that they require manual effort to update.

* JSON Schema
* OpenAPI
* AsyncAPI
* API Blueprint
* Thrift

SPEQ allows you to reference any of these definitions where they are typically maintained with the goal of providing tools to compile these schemas into SPEQ and from SPEQ into authoriative defintiions when updated... providing you the flexibility to replace all your definitions with SPEQ when the time is right.

