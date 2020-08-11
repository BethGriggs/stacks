### Airgap Support 

This document wil describe how you can use this Stack in a airgap environment.

# Using an internal OS repository

# Overriding Node.js headers download location

# Using a custom npm registry

This is covered by [npm documentation](https://docs.npmjs.com/docker-and-private-modules#create-and-check-in-a-project-specific-npmrc-file).

You will need to create a custom `.npmrc` file and copy it into your container.

Add the following to copy the .npmrc file in to the Dockerfile:

```
ARG NPM_TOKEN  
COPY .npmrc .npmrc
```

It would be prudent to remove the `.npmrc` from the container after your `npm install` command:

```
RUN rm -f .npmrc
```

You'd then need to run the build with 
`docker build --build-arg NPM_TOKEN=${NPM_TOKEN} .`