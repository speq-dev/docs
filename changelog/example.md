# Example

{% tabs %}
{% tab title="YAML" %}
```yaml
changelog:
  2030-01-01T00:00:00Z: # ISO-8601, UTC Time Zone
    new:
      $.resources["/admin/users/{id}/profile"].post.ProfileUpdate: #JSONPath
        description: ''
        author: ''
    removed: 
      $.resources["/profiles"].post.ProfileUpdate:
        description: ''
        author: ''
    changed: 
      $.resources["/profiles"].post.ProfileUpdate:
        description: ''
        author: ''
        before: {}
        after: {}      
```
{% endtab %}

{% tab title="JSON" %}
```javascript
{
   "changelog": {
      "Mon Dec 31 2029 19:00:00 GMT-0500 (EST)": {
         "new": {
            "$.resources[\"/admin/users/{id}/profile\"].post.ProfileUpdate": {
               "description": "",
               "author": ""
            }
         },
         "removed": {
            "$.resources[\"/profiles\"].post.ProfileUpdate": {
               "description": "",
               "author": ""
            }
         },
         "changed": {
            "$.resources[\"/profiles\"].post.ProfileUpdate": {
               "description": "",
               "author": "",
               "before": {},
               "after": {}
            }
         }
      }
   }
}
```
{% endtab %}
{% endtabs %}

