# Jamsocket Deploy Action 🚀

Automatically deploy session backend code to your Jamsocket service.

## Configuration

To use this Jamsocket deploy action, add the action to your [Github Workflow](https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization#creating-a-starter-workflow).

Here's an example of an action that will run whenever code is pushed to `main`. This action would live under the `.github/workflows` folder.

```yaml
name: Deploy to Jamsocket
on:
  push:
    branches: [ "main" ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Deploy to Jamsocket
        uses: jamsocket/jamsocket-deploy-action@v0.1.0
        with:
          jamsocket_api_token: ${{ secrets.JAMSOCKET_API_TOKEN }}
          jamsocket_account: my-jamsocket-account
          jamsocket_service: my-jamsocket-service
          docker_build_context: ./server
          dockerfile_path: ./server/Dockerfile
```

### Required Setup

The following options must be configured in order to make a deployment. As show in the example above, the following options are added under the `with` section of your `Deploy to Jamsocket` step.

| Key | Value Information | Type| Required |
|----------|----------|----------|----------|
| jamsocket_api_token | Your API token for Jamsocket authentication, which you can find in [Settings](https://app.jamsocket.com/settings) under Access Tokens. Store this API token as a [secret](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-encrypted-secrets).  | `with` | Yes |
| jamsocket_account | The name of your Jamsocket account, which can be found in [Settings](https://app.jamsocket.com/settings) under Account > name. | `with`| Yes |
| jamsocket_service | The name of the Jamsocket service you are pushing your code to. | `with` | Yes |
| docker_build_context | The path to your Docker build context, which should be the same as the WORKDIR specified in your Dockerfile. | `with` | Yes |
| dockerfile_path | The path to your Dockerfile. | `with` | Yes |

## Deployment

When a Jamsocket deployment is successful, you will find that a new image has been pushed to your Jamsocket service. You can find new images on the service page under `Docker Images`.
