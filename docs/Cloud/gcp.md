# GPC - Google Cloud Provider

[Sapmles of functions](https://github.com/firebase/functions-samples)

Google Cloud Deployment Manager - gcloud sdk

gcloud - manage Google Cloud resources and developer workflow

<https://cloud.google.com/sdk/gcloud/reference>

```sh
docker pull kasmweb/ubuntu-bionic-desktop:1.10.0
europe-west1-docker.pkg.dev/project-name/registry-name/nginx

gcloud auth login
gcloud config set project VALUE
gcloud projects list
```

## Cloud Build

<https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration#yaml>

## How to check docker image platform

```sh
docker image inspect <image id>
```

## Getting an issue with port number

Issue:

> The user-provided container failed to start and listen on the port defined provided by the PORT=80 environment variable. Logs for this revision might contain more information.

Probably it's because of M1 processor.

First check your image platform:

```sh
docker image inspect <image id>
```

To solve issue, try this tip:

> Build/Pull your Docker container/image with the --platform linux/amd64 flag before deploying the image to Cloud Run.

```sh
docker pull kasmweb/ubuntu-bionic-desktop:1.10.0 --platform linux/amd64
docker buildx build --platform linux/amd64 -t TAG_NAME .
```

deploy:

<https://cloud.google.com/run/docs/deploying#service>

gcloud run deploy --image=gcr.io/<MY_PROJECT_ID>/thecodingmachine/gotenberg:6 \
  --port=3000 --region=us-central1 --allow-unauthenticated --platform=managed \
  --command=gotenberg gotenberg

## CLI Commands

[CLI Documentation](https://firebase.google.com/docs/cli)

## Run local functions using different port

```bash
firebase serve --only functions --port=9000
```

## How to deploy docker application to Cloud Run

```sh
docker pull busybox
docker tag busybox europe-west1-docker.pkg.dev/project-name/registry-name/busybox
docker push europe-west1-docker.pkg.dev/project-name/registry-name/busybox

gcloud auth login
gcloud config set project project-name
gcloud auth configure-docker
```

## GCP SDK

<https://cloud.google.com/nodejs/docs/reference>

### Cloud Run vs App Engine

For low-traffic applications, Cloud Run is dramatically cheaper than App Engine.

Cloud Run runs containers, so for each release you have to build a container and push it to GCP. Unlike App Engine, Cloud Run only runs when requests come in, so you don’t pay for time spent idling.

### Compute Engine vs App Engine

<https://tutorialsdojo.com/google-compute-engine-vs-app-engine/>

## Products

### Google Cloud Deployment Manager



### Google Container Registry

<https://cloud.google.com/container-registry?hl=en-GB>

Hostname | Storage location
gcr.io | Stores images in data centers in the United States
asia.gcr.io | Stores images in data centers in Asia
eu.gcr.io | Stores images in data centers within member states of the European Union
us.gcr.io | Stores images in data centers in the United States

### Cloud Deployment Manager

### Cloud Deployment Manager V2

### Compute Engine

Compute Engine delivers configurable virtual machines running in Google’s data centers with access to high-performance networking infrastructure and block storage solutions.

### App Engine

App Engine is a fully managed, serverless platform for developing and hosting web applications at scale. AE is a traditional hosting platform: it runs continuously and serves requests as they come in. At the end of the month, you pay for the amount of time it was running, which is typically “the entire month”.

### Cloud Run

Cloud Run runs containers, so for each release you have to build a container and push it to GCP. Unlike App Engine, Cloud Run only runs when requests come in, so you don’t pay for time spent idling.
