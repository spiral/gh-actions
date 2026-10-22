<p align="center">
    <img src="https://user-images.githubusercontent.com/2461257/112313394-d926c580-8cb8-11eb-84ea-717df4e4d167.png" width="400" alt="Spiral Framework">
    <h1 align="center">Spiral Framework GitHub Actions</h1>
    <br>
</p>


## General usage

This package allows us to reuse GitHub actions, which simplifies version management.

### Example of use of the action [PHPUnit](https://github.com/sebastianbergmann/phpunit)

```yml
on:
  push:
    branches:
      - master
      - '*.*'
  pull_request: null
  
name: phpunit

jobs:
  phpunit:
    uses: spiral/gh-actions/.github/workflows/phpunit.yml@master
    with:
      # coverage: pcov / coverage: xdebug / coverage: xdebug2 / coverage: none 
      # extensions: pdo, pdo_pgsql
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1']
      #tools: composer:v2 
```

### Example of use of the action [PSALM](https://github.com/vimeo/psalm)

```yml
on:
  push:
    branches:
      - master
      - '*.*'
  pull_request: null

name: static analysis

jobs:
  psalm:
    uses: spiral/gh-actions/.github/workflows/psalm.yml@master
    with:
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1']
```

### QA tools as [bamarni/composer-bin-plugin](https://github.com/bamarni/composer-bin-plugin) tools

`psalm.yml` and `cs-fix.yml` install a bin tool when `<target-directory>/<bin-tool>/composer.json` exists
(`target-directory` from `extra.bamarni-bin`, `vendor-bin` by default; `bin-tool` is `psalm` / `code-style` by default)
and pick its config from the same directory (`psalm.xml` / `.php-cs-fixer.dist.php`); the `config` input overrides it.
The tool is installed for the `php` input version, so that version has to satisfy the tool's PHP requirement.
For psalm, `php` is only the runtime. With a Psalm bin tool, Psalm analyses the code for the minimum PHP from
`require.php` in composer.json, as a local run does, whatever the runtime version is.
Set `analysis-php` (for example `'8.2'`) to analyse for another version.
Repositories without a tool directory work as before.

### Example of use of the action [Coding standarts](https://github.com/spiral/code-style)

```yml
on:
  push:
    branches:
      - master
      - '*.*'
  pull_request: null

name: coding standards

jobs:
  coding-standards:
    uses: spiral/gh-actions/.github/workflows/cs.yml@master
    with:
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1']
```

License:
--------
MIT License (MIT). Please see [`LICENSE`](./LICENSE) for more information. Maintained by [Spiral Scout](https://spiralscout.com).
