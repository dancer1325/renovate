---
title: Datasources
---

# Datasources

* how does it work?
  * Renovate's manager 
    * -- scan the -- files
    * -- extracted the -- dependencies
    * 👀-- assigns a -- `datasource` / EACH extracted package file or dependency 👀
* uses
  * 💡tells Renovate -- how to search for -- NEW versions 💡
    * _Example:_ | `packageRules` array, to configure Renovate's behavior
        ```json
        {
          "packageRules": [
            {
              "matchDatasources": ["npm"],
              "matchPackageNames": ["lodash"],
              "automerge": true
            }
          ]
        }
        ```

## Supported Datasources

<!-- Autogenerate in https://github.com/renovatebot/renovate -->
<!-- Autogenerate end -->
