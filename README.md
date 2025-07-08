# GitHub Action to Docker Build

![https://github.com/zmicro-design/action-vercel-deploy](https://img.shields.io/github/v/release/zmicro-design/action-vercel-deploy)
![https://github.com/zmicro-design/action-vercel-deploy](https://github.com/zmicro-design/action-vercel-deploy/workflows//Publish/badge.svg)

### Usage

| option | required | description |
| ------ | -------- | ----------- |
| token  | true     | vercel token. You can get it from https://vercel.com/account/tokens |
| org-id | false | vercel organization id. See project settings page -> General -> Team ID |
| project-id | false | vercel project id. See project settings page -> General -> Project ID |

### Example

```yml
name: CI

on: [push]

jobs:
  build:
    name: Test
    runs-on: ubuntu-latest
    steps:
      - name: Vercel Deploy
        uses: zmicro-design/action-vercel-deploy@v1
        with:
          token: ${{ secrets.VERCEL_TOKEN }}
          org-id: ${{ secrets.VERCEL_ORG_ID }}
          project-id: ${{ secrets.VERCEL_PROJECT_ID }}
```

### License

[MIT](./LICENSE)
