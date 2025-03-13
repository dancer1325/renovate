---
title: Presets
description: Learn about Renovate configuration presets
---

* goal
  * Renovate configuration presets
    * describe
    * why to use them

## Use cases

- Set up the bot with good default settings
- Avoid duplicating your configuration
- Share your configuration -- with -- others
- Use somebody else's configuration as-is OR extend it -- with -- your OWN rules

## How to use ?

* _Example1:_ if you're using the `config:recommended` preset & want to pin your GitHub Action digests -> 
  * search the docs
  * add `helpers:pinGitHubActionDigests` preset

    ```json
    {
      "extends": ["config:recommended", "helpers:pinGitHubActionDigests"]
    }
    ```

<!-- prettier-ignore -->
!!! tip
    If there is a logical conflict between presets, then the _last_ preset in the `"extends"` array "wins".

## Managing config / MANY repositories

* recommendations
  * Create a GLOBAL preset configuration
    * -> ONLY need -- to edit -- 1!
  * | ALL repositories / should use your global preset as base -> extend -- from the -- global preset

## Presets are modular

* == 
  * small OR large -- as you -- need
  * -- extend from -- OTHER presets

## Built-in presets

* see [Renovate's default presets](../presets-default.md)

### How to add ANOTHER built-in?

* see [Contributing to presets](../config-presets.md#contributing-to-presets)
