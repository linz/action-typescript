# linz/action-typescript

Composite action to checkout/build/test and npm/yarn package

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
    uses: linz/action-typescript/.github/workflows/main.yml@v1
    with:
      node-version: "18.x"
      registry-url: "https://npm.pkg.github.com"
      package-manager: "yarn"

  composite-action:
    runs-on: ubuntu-latest
    steps: 
      - name: Build and test
        uses: linz/action-typescript@v1
        with:
          node-version: "18.x"
          registry-url: "https://npm.pkg.github.com"
          package-manager: "yarn"
```