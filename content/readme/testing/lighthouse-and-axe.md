---
title: Lighthouse audits on Bitbucket Pipeline
date: 2021-04-16T21:20:06.000+00:00
draft: true
---

I found a guide on how to run Lighthouse CLI on Bitbucket Pipelines, https://blog.vianetz.com/2021/01/google-lighthouse-bitbucket-pipelines/.

First we need to define the pipeline in our repository. We do this by creating a `bitbucket-pipeline.yml`.

My first goal is to create a pipeline only runs by triggering it manually on the Bitbucket site. To do this I define a custom pipeline:

```
image: node:12.2

pipelines:
  custom:
    lighthouse-checks:
      - step:
		      name: Lighthouse Checks
          caches:
            - node
          script:
            - apt-get update && apt-get install apt-transport-https -y
            - wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
            - sh -c 'echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
            - apt-get update && apt-get install google-chrome-stable -y
            - npm i -g @lhci/cli@"^0.7.0"
            - lhci healthcheck
            - lhci collect --url $LIGHTHOUSE_URL
            - lhci assert
            - mv .lighthouseci lighthouse-results
          artifacts:
            - lighthouse-results/**
					 
```

For NUXT project I found: https://github.com/samturrell/nuxt-lighthouse-module

## Lighthouse CLI
Install the CLI via NPM:
```
npm install -g @lhci/cli@0.7.x
```

And to run it:
```
lhci collect --isSinglePageApplication --url https://www.capcito.com/sv
```
Here I use the flag for single page application and the url to the page I want to test.

The command will output the report inside the folder `.lighthouseci` as `.html` and `.json`

## Lighthouse Server
https://github.com/GoogleChrome/lighthouse-ci/blob/main/docs/server.md

## Axe CLI
Install the CLI via NPM:
```
npm install -g @axe-core/cli
```

And to run it:
```
axe https://qa.capcito.com
```

A useful flag to use is the exclude selector flag `-e` for when you have external markup that you have no control over.