# linz/action-typescript

Composite action to checkout/build/test typescript with npm or yarn.

usage: 

```yaml
 - name: Build and test
   uses: linz/action-typescript@v2
```

Example github action, using both the composite action and reusable workflow

```yaml
name: push

on: 
  push:

jobs:
  reusable-workflow:
    uses: linz/action-typescript/.github/workflows/main.yml@v2
    with:
      node-version: "18.x"
      registry-url: "https://npm.pkg.github.com"
      package-manager: "npm"

  composite-action:
    runs-on: ubuntu-latest
    steps: 
      - name: Build and test
        uses: linz/action-typescript@v2
        with:
          node-version: "18.x"
          registry-url: "https://npm.pkg.github.com"
          package-manager: "npm"
```