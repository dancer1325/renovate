# String Pattern Matching - Regex or Glob

* uses
  * | SOME configuration options
    * if there are MULTIPLE inputs (_Example:_ managers / have MULTIPLE categories) & SOME matcher matches -> returns `true` 
* ALLOWED
  * [`minimatch`](https://github.com/isaacs/minimatch) glob patterns + exact strings matches, OR
  * regular expression (regex) patterns
* | through time, it has evolved
  * ❌EXISTING configurations -- could NOT be ENTIRELY consistent with -- EACH other ❌
    * Reason: 🧠can have a MIX of approaches 🧠

## `*`

* == "match EVERYTHING"
* restrictions
  * ❌ \+ positive or negative match, NOT valid ❌ 
* _Examples:_
  * _Example1:_ 
    ```json title="Example of valid wildcard use"
    {
      "allowedEnv": ["*"]
    }
    ```
  * _Example2:_ ❌NOT valid ❌
    * Reason: 🧠 + additional match 🧠
    ```json title="Example of invalid wildcard use with additional match"
    {
      "allowedEnv": ["*", "ABC"]
    }
    ```
  * _Example3:_ ❌NOT valid ❌
    * Reason: 🧠 + additional match 🧠
    ```json title="Example of invalid wildcard use with negation"
    {
      "allowedEnv": ["*", "!ABC"]
    }
    ```

## Regex matching

* requirements
  * starts with 
    * `/` OR
    * `!/`
  * ends with
    * `/` OR
    * `/i`

### case sensitive

* by default
* if you want to ignore it -> set the `i` flag

### 👀-- uses -- re2 syntax 👀

* [`re2` library](https://github.com/google/re2)
* != FULL regex specification
  * Reason: 🧠DIFFERENT syntax/support 🧠

### Example regex patterns

| Pattern   | Regex pattern explanation                                               |
| --------- | ----------------------------------------------------------------------- |
| `/^abc/`  | matches any string starting with lower-case `abc`                       |
| `/^abc/i` | matches any string starting with `abc` in lower or upper case, or a mix |
| `!/^a/`   | matches any string not starting with `a` in lower case                  |

### [regex101.com](https://regex101.com/?flavor=javascript&flags=ginst)

* == patterns interactively online tool 
* uses
  * testing your patterns
* if you want to convert regex | regex101 -- to -- Renovate config
  * escape the backslashes (`\`)
    * _Example:_ `\n\s` --> `\\n\\s`

## Glob matching

* if string provided != regex pattern -> it's 
  * a glob pattern
  * -- parsed via -- `minimatch` library

### case-insensitive

* ❌NOT possible to adjust it ❌

### Example

| Pattern     | Glob pattern explanation                                     |
| ----------- | ------------------------------------------------------------ |
| `abc123`    | matches `abc123` exactly, or `AbC123`                        |
| `abc*`      | matches `abc`, `abc123`, `ABCabc`, but not `abc/def`         |
| `abc**/*`   | matches `abc/def` but not `abc`, `abcd`, or `abc/def/ghi`,   |
| `abc**/**`  | matches `abc/def` and `abc/def/ghi`, but not `abc` or `abcd` |
| `abc{/,}**` | matches `abc`, `abcd`, `abc/def`, and `abc/def/ghi`          |

## Negative matching

* "Positive" matches
  * == patterns (glob or regex) / NOT start with `!`
  * | array of patterns
    * if SOME "Positive" matches is included & you want to return `true` -> >=1 must match
* "Negative" matches
  * == patterns / start with `!`
    * _Example:_ `!/^a/`, `!b*`
    * 👀if you need to positive-match & starts with `!` -> use regular expression pattern 👀
      * _Example:_ pattern `"!abc"`
        * `["/^!abc$/"]` positively match  
  * | array of patterns
    * if SOME "Negative" matches is included & you want to return `true` -> NONE must match
      * _Example:_ pattern `["/^abc/", "!/^abcd/", "!/abce/"]`
        * matches `"abc"` and `"abcf"`
        * NOT match `"foo"`, `"abcd"`, `"abce"`, or `"abcdef"`
