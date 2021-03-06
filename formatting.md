# Formatting

SPEQs are formatted as `JSON` or `YAML` and should always have a `.speq` extension.

Because `YAML` is a superset of `JSON` in any tooling you have you can simply set syntax highlighting and validation to `YAML` and it will perform basic syntax validation and highlighting of any SPEQ. 

{% hint style="info" %}
If you plan to consume SPEQ programatically, assuming the file is `YAML` and using `YAML` parsing libraries will allow you to avoid additional detection logic.  
{% endhint %}

The custom `.speq` extension enables improvements like intellisense and custom syntax \(e.g. references\) highlighting down the line.

{% hint style="danger" %}
YAML-specific features like multiple documents in a single file and templating are not supported.
{% endhint %}

## Special Properties

| Property | Description |
| :--- | :--- |
| `$import` |  |
| `$extend` |  |
| `$ref` |  |

