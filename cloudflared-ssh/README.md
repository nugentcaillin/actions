# Action to run shell commands on a remote machine protected with cloudflare access
Uses cloudflare service credentials to connect via ssh
## Requires
- A cloudflare access client ID and secret. These are created using the service
    credentials in cloudflare one, under access controls. They must be mentioned
    in a policy that applies to the target (host server)
## Usage
```console
jobs:
  deploy_to_server:
    runs-on: ubuntu-latest
    steps:
      - uses: nugentcaillin/actions/cloudflared-ssh@main
        with:
          id: ${{secrets.CF_ACCESS_CLIENT_ID}} # cloudflare access ID
          secret: ${{secrets.CF_ACCESS_CLIENT_SECRET}} # cloudflare access secret
          key: ${{secrets.DEPLOY_BOT_PRIVATE_KEY}} # private key to use for ssh
          user: ${{secrets.SSH_USER}} # ssh user
          host: ${{secrets.SSH_HOST}} # ssh host
          script: |
            # commands to run
            # on host machine
```
