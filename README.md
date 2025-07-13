# GitHub Action to Vercel Deploy

![https://github.com/zmicro-design/action-vercel-deploy](https://img.shields.io/github/v/release/zmicro-design/action-vercel-deploy)
![https://github.com/zmicro-design/action-vercel-deploy](https://github.com/zmicro-design/action-vercel-deploy/workflows//Publish/badge.svg)

### Usage

#### Inputs

| option | required | default | description |
| ------ | -------- | ------- | ----------- |
| token  | true     | -       | vercel token. You can get it from https://vercel.com/account/tokens |
| org-id | false    | -       | vercel organization id. See project settings page -> General -> Team ID |
| project-id | false | -       | vercel project id. See project settings page -> General -> Project ID |
| environment | false | preview | vercel deployment environment |
| git-branch | false | -       | vercel git branch for pulling |
| deploy-archive | false | -       | vercel deploy to compress the deployment code into an archive before uploading it |
| debug | false | false   | enable debug mode for vercel deployment |

#### Outputs

| output | description |
| ------ | ----------- |
| preview-url | preview url |

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
        id: vercel-deploy
        uses: zmicro-design/action-vercel-deploy@v1
        with:
          token: ${{ secrets.VERCEL_TOKEN }}
          org-id: ${{ secrets.VERCEL_ORG_ID }}
          project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          environment: preview
          git-branch: ${{ github.head_ref || github.ref_name }}
          deploy-archive: true
          debug: ${{ secrets.ACTIONS_STEP_DEBUG || false }}
      
      - name: Get Preview URL
        run: echo "Preview URL: ${{ steps.vercel-deploy.outputs.preview-url }}"
```

### License

[MIT](./LICENSE)
