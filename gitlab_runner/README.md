# Overview
Run gitlab runner as a docker container with access to the docker daemon on the host machine.

### Config templates
- `docker-shared.toml`:
Use docker executor with access to the host docker daemon, which does not need docker-in-docker (dind) for docker builds (faster and more optimised build cache, at the expense of less isolation).

# Setup
- `export GITLAB_URL=<gitlab-url>`
- `export GITLAB_RUNNER_TOKEN=<gitlab-runner-token>`
- `export CONFIG_TEMPLATE=docker-shared.toml`
- `docker compose up -d`
- `docker compose exec gitlab-runner gitlab-runner register \`\
    `--non-interactive \`\
    `--template-config /etc/gitlab-runner/$CONFIG_TEMPLATE \`\
    `--url $GITLAB_URL \`\
    `--token $GITLAB_RUNNER_TOKEN \`
