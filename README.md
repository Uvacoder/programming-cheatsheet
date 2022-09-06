# Website

This website is built using [Docusaurus 2](https://docusaurus.io/), a modern static website generator.

### Installation

```
$ yarn
```

### Local Development

```
$ yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Build

```
$ yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

### Deployment

Docker:

```sh
docker build -t programming-cheatsheet . --platform linux/amd64
docker tag programming-cheatsheet europe-west1-docker.pkg.dev/call-me-cube/docker-registry/programming-cheatsheet:latest
docker push europe-west1-docker.pkg.dev/call-me-cube/docker-registry/programming-cheatsheet:latest
gcloud run deploy --image=europe-west1-docker.pkg.dev/call-me-cube/docker-registry/programming-cheatsheet:latest \
  --port=80 --region=us-central1 --allow-unauthenticated --platform=managed \
  programming-cheatsheet
```

docker run -d -p 3000:3000 programming-cheatsheet

Using SSH:

```
$ USE_SSH=true yarn deploy
```

Not using SSH:

```
$ GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.
