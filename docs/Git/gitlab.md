# GitLab

## Difference between cache and artifacts

<https://docs.gitlab.com/ee/ci/caching/>

## How to store ssh keys and ssh or scp to remote server from gitlab runner docker executor

<https://docs.gitlab.com/ee/ci/ssh_keys/>

```ci
deploy_www:
  stage: deploy
  needs: [build_nextjs]
  only:
    - master
  script:
    - 'command -v ssh-agent >/dev/null || ( apt-get update -y && apt-get install openssh-client -y )'
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -
    - mkdir -p ~/.ssh
    - chmod 700 ~/.ssh
    - tar -cf deployment.tar .next next.config.js package.json package-lock.json node_modules
    - scp -o StrictHostKeyChecking=no /deployment.tar root@10.10.10.10:/var/www/deployment.tar
    - ssh -o StrictHostKeyChecking=no root@10.10.10.10 'mkdir -p /var/www/beonepayment.com/deployment | tar
```

## Artifacts | Cache

```ci
build:
    stage: build
    script:
        - npm install
    artifacts:
        name: "${CI_BUILD_REF}"
        expire_in: 10 mins
        paths:
            - node_modules
```

## Run code on specific case - when to run code

<https://docs.gitlab.com/ee/ci/jobs/job_control.html>

<https://docs.gitlab.com/ee/ci/pipelines/merge_request_pipelines.html>

```sh
job:
  script: echo "Hello, Rules!"
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      when: manual
      allow_failure: true
    - if: '$CI_PIPELINE_SOURCE == "schedule"'
```

## Run pipe on specific changes and use different configuration within project

<https://docs.gitlab.com/ee/ci/pipelines/pipeline_architectures.html>
