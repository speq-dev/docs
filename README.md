---
description: The 'universal spec' has arrived
---

# What is SPEQ?

**SPEQ** is a definition to describe APIs, services and databases in a **protocol-agnostic** manner. 

That means SPEQ can act as the defacto definition for REST, GraphQL, Kafka, gRPC, SQL and any other service that follows a client-server model within your organization or team.

SPEQ is backed by a terminal utility, [**Speqqy**](https://www.npmjs.com/package/speqqy) with plans to support: 

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

## The 

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
      <td style="text-align:left">SPEQ</td>
      <td style="text-align:left">
        <p><b>Required</b>
        </p>
        <p>Describes servers, versions, development stages, governance rules, resources,
          operations and message/metadata schemas for one or more services.</p>
      </td>
      <td style="text-align:left"><code>*.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Definition</td>
      <td style="text-align:left">
        <p><b>Auto-Generated</b>
        </p>
        <p>When a SPEQ is compiled, all references are resolved, external schemas
          and specifications are converted, rules will be validated and one definition
          will be generated for each service and it&apos;s associated stages and
          versions, preventing exposure of internal services and descriptions.</p>
      </td>
      <td style="text-align:left"><code>{service}-{stage}-{version}.def.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Change Log</td>
      <td style="text-align:left">
        <p><b>Auto-Generated</b>
        </p>
        <p>An auto-generated list of changes, generated at compile time between the
          previous SPEQ and the current. Useful for generating release notes.</p>
      </td>
      <td style="text-align:left"><code>*.changelog.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Sample</td>
      <td style="text-align:left">Describes a sample payload (message &amp; metadata) that conforms to a
        SPEQ definition (and can represent a server message for virtualization!)</td>
      <td
      style="text-align:left"><code>*.sample.speq</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Tests</td>
      <td style="text-align:left">Describe one or more service functional, end-to-end or contract tests,
        referencing SPEQs that can be used by vendors and tooling to automate testing.</td>
      <td
      style="text-align:left"><code>*.tests.speq</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Virts</td>
      <td style="text-align:left">Describe virtualized service configuration, that can be used by vendors
        and tooling to stand up a virtualized instance of your services.</td>
      <td
      style="text-align:left"><code>*.virts.speq</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Props</td>
      <td style="text-align:left">A collection of freeform data objects that can be referenced in SPEQ tests,
        virts and scenarios.</td>
      <td style="text-align:left"><code>*.props.speq</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Protocol</td>
      <td style="text-align:left">A SPEQ that describes the unique properties of a service or API.
        <br />
        <br />For example:
        <br />
        <br />Should it support client streaming?
        <br />What metadata does it support?
        <br />Does the API require serialization and deserialization?
        <br />
        <br />A set of default proto SPEQs are defined (e.g. for REST, GraphQL, gRPC,
        Kafka), but custom protocols can be defined at any time, but should be
        prefixed with <code>x-</code>
      </td>
      <td style="text-align:left"><code>*.proto.speq</code>
      </td>
    </tr>
  </tbody>
</table>

## What about edge cases?



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

