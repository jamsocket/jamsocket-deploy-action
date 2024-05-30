# Jamsocket Deploy Action

Automatically deploy session backend code to your Jamsocket service.

### Required Setup

The following options must be configured in order to make a deployment.

| Key | Value Information | Type| Required |
|----------|----------|----------|----------|
| jamsocket_api_token | Your API token for Jamsocket authentication, which you can find in [Settings](https://app.jamsocket.com/settings) under Access Tokens. Store this API token as a [secret](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-encrypted-secrets).  | `with` | Yes |
| jamsocket_account | The name of your Jamsocket account, which can be found in [Settings](https://app.jamsocket.com/settings) under Account > name. | `with`| Yes |
| jamsocket_service | The name of the Jamsocket service you are pushing your code to. | `with` | Yes |
| docker_build_context | The path to your Docker build context, which should be the same as the WORKDIR specified in your Dockerfile. | `with` | Yes |
| dockerfile_path | The path to your Dockerfile. | `with` | Yes |
