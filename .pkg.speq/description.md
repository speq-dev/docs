# Description

When a `.def.speq` is compiled into a `.pkg.speq` with `speqqy`

* any rules are validated 
* all external references are resolved & merged in \(e.g. if you created a unique `.def.speq` for each service\)
* external schemas and specifications are converted \(e.g. OpenAPI specifications that are referenced will be parsed and converted into SPEQ\)
* by default, to prevent exposure of internal resources and details, a package will be generated for
  * each service 
  * each development stage \(e.g. production vs. staging\)
  * each version \(e.g. v2, v3\)

