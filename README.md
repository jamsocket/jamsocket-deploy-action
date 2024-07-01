# Jamsocket Deploy Action 🚀

Automatically deploy session backend code to your Jamsocket service.

## Configuration

To use this Jamsocket deploy action, add the action to your [Github Workflow](https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization#creating-a-starter-workflow).

Here's an example of an action that will run whenever code is pushed to `main`.

To use this example, paste the code snippet below in a file called `deploy.yml`. Add that file to the `.github/workflows` directory in the root of your repository. When you push your code to `main`, you can view the running action in the `Actions` tab of your Github repository.

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
        uses: jamsocket/jamsocket-deploy-action@v0.1.1
        with:
          jamsocket_api_token: ${{ secrets.JAMSOCKET_API_TOKEN }}
          jamsocket_account: my-jamsocket-account
          jamsocket_service: my-jamsocket-service
          docker_build_context: ./server
          dockerfile_path: ./server/Dockerfile
```

### Required Setup

The following options must be configured in order to make a deployment. As shown in the example above, the following options are added under the `with` section of your `Deploy to Jamsocket` step.

| Key | Value Information | Type| Required |
|----------|----------|----------|----------|
| jamsocket_api_token | Your API token for Jamsocket authentication, which you can generate in [Settings](https://app.jamsocket.com/settings) under Access Tokens. Store this API token as a [secret](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-encrypted-secrets) in your repository's Settings page under Security > Secrets and variables > Actions > Repository secrets. | `with` | Yes |
| jamsocket_account | The name of your Jamsocket account, which can be found in [Settings](https://app.jamsocket.com/settings) under Account > name. | `with`| Yes |
| jamsocket_service | The name of the Jamsocket service you are pushing your code to. | `with` | Yes |
| docker_build_context | The path to the directory that your [Docker build should access](https://docs.docker.com/build/building/context/). This is often the directory the Dockerfile is in. | `with` | Yes |
| dockerfile_path | The path to your Dockerfile. | `with` | Yes |
| tag | A custom tag to apply to the image. If provided, this image will only be used when this tag is provided in the spawn request. This can be used for preview deploy-like functionality. | `with` | No |

## Deployment

When a Jamsocket deployment is successful, you will find that a new image has been pushed to your Jamsocket service. You can find new images in the [Jamsocket dashboard](https://app.jamsocket.com/home) on the service page under `Docker Images`.
