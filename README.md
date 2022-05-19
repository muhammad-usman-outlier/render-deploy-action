# Fetch and verify Render deploy 

This action fetches Render deploy links from PR and verifies for a successful deployment of the deloyment preview.

## Inputs

## `token`

**Required** Github Token.

## `render-email`

**Required** Email for Render Dashboard.

## `render-password`

**Required** Password for Render Dashboard.
 
## `sleep`

Sleep time between the render deployment success and setting the Github deployment as successful.
 `"0"`.
## `retries`

**Required** Maximum number of retries trying to find the deployment. Note: Retries will be attempted every 5 seconds.
 `"50"`.
## `wait`

**Required** Sleep time between retries to find Render deployments statuses.
 `"8000"`.

## Outputs

## `preview-url`

The successfully deployed preview link.

## Example usage

```yaml
name: Fetch and verify Render deploy
on: [pull_request]:
jobs:
  deploy:
    name: Wait for Render Deployment
    runs-on: ubuntu-18.04
    steps:
      - name: Render Deploy Action
        id: render-deploy
        uses: muhammad-usman-outlier/render-deploy@v1.1
        with: 
            token:
            render-email:
            render-password:

  ```