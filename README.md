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
        ['8.1', '8.2']
      stability: >-
        ['prefer-lowest', 'prefer-stable']
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
