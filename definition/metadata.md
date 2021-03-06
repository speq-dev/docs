---
description: Optional metadata about your SPEQ
---

# metadata

{% tabs %}
{% tab title="YAML" %}
```yaml
metadata:
  package:
    acme:
      title: Acme Corporation
      description: All APIs within Acme Corporation
      deprecated: false
  runtimes:
    speq: 
      version: '1.0.0-draft'
```
{% endtab %}

{% tab title="JSON" %}
```javascript
{
  "metadata": {
    "package": {
      "acme": {
        "title": "Acme Corporation",
        "description": "All APIs within Acme Corporation",
        "deprecated": false
      }
    },
    "runtimes": {
      "speq": {
        "version": "1.0.0-draft"
      }
    }
  }
}
```
{% endtab %}
{% endtabs %}



