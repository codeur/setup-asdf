# asdf cache action

A GitHub Action that install [`asdf`] and all runtimes from `.tool-versions`.

It is a wrapper for [`asdf-vm/actions/install`] with a caches for `asdf`.

[`asdf-vm/actions/install`]: https://github.com/asdf-vm/actions
[`asdf`]: https://github.com/asdf-vm/asdf

```yml
      - name: Install tools from asdf config
        uses: codeur/setup-asdf@v1
```

---

<img src="https://cdn.evilmartians.com/badges/logo-no-label.svg" alt="" width="22" height="16" />  Made at <b><a href="https://evilmartians.com/devtools?utm_source=asdf-cache-action&utm_campaign=devtools-button&utm_medium=github">Evil Martians</a></b>, product consulting for <b>developer tools</b>.

---


## Full Example

```yml
name: CI
on:
  push:
    branches:
      - main
  pull_request:
permissions:
  contents: read
jobs:

  test:
    name: Test
    runs-on: ubuntu-latest
    steps:
      - name: Checkout the repository
        uses: actions/checkout@v4
      - name: Install tools from asdf config
        uses: codeur/setup-asdf@v1
      - name: Run tests
        run: pnpm test
```


## Inputs

You can uses inputs to specify explicitly versions to use. Be careful, for now,
you must specify both `ruby-version` and `nodejs-version` if you want to use them.
A `.tool-versions`file is written by action before running `asdf install`.


```yml
      - name: Install tools from asdf config
        uses: codeur/setup-asdf@v1
        with:
          ruby-version: 3.1
          nodejs-version: 20
```
