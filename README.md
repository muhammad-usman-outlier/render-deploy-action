# Render Deploy Action

### The action performs the following tasks
- Fetches PR comment by matching against Render's comment content.
- Extracts URLs from comment.
- Makes an API call to Render for tracking deployment Progress using service-id extracted from Progress URL.
- Awaits Deployment status.

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
        uses: muhammad-usman-outlier/render-deploy-action@v1.0.0
        with: 
            token:
            render-email:
            render-password:

  ```
  
  ## Contribute
  
  GitHub Actions are run from repos, so we have to run [ncc](https://github.com/zeit/ncc) to generate the packaged dist
  
  ```bash
$ npm run all
$ git add .
$ git commit -m "My Render Deploy Action Release"
$ git tag -a -m "My Render Deploy Action Release" v2.0.0
$ git push --follow-tags
```
