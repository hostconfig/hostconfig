# hostconfig
Welcome to hostconfig.

'hostconfig' is a template project aiming to demonstrate how to launch multiple services concurrently, whether via your 'localhost' address or on a remote machine, within the infrastructure of a single web application.

## quickstart

```
$ docker compose up --build

building 0...100%

http server listening on http://localhost:8080
https server listening on https://localhost:443

$ docker compose down
```

## About hostconfig

This master project contains the following sub-projects:

- hostconfig/app
- hostconfig/http
- hostconfig/https
- hostconfig/public
- hostconfig/static

Each sub-project exports a NodeJs module, written in Typescript and compiled to Javascript.

Each of these modules provides either a service (i.e., an http server) or some content that the service(s) can provide (i.e., static HTML pages or an express app).

This master project consumes each of these module sub-projects as NPM/Yarn workspaces, managed as git submodules.

Thus it is possible, from this master project, to spin up each of the available services concurrently, allowing for the various content to be served, accessed, and managed over a variety of different connection protocols, ports, and methods, all running as a single web application.

For example:

```
$ docker compose up --build

building 0...100%

http server listening on http://localhost:8080
https server listening on https://localhost:443

$ docker compose down
```

More services and content can be easily added to the 'src' directory, such as a database server and api routes (coming soon).

The content and functionality of 'hostconfig' - and it's sub-projects - is kept minimal, intended as a reference or a starting point for building larger, full-featured web applications from.

The primary technical goal is to implement a highly modular application infrastructure, which allows for services and content to be easily added, removed, launched and managed from a singular interface, in an almost "plug'n'play" fashion.

Additionally, each of the 'service provider' sub-projects are designed to function independently of the master project, where possible.

## Further information

*NOTE:* the 'https' module requires an additional build step to generate the required self-signed TLS certificates, which must also be installed in your browser and/or client - [full instructions are available in the project repository](https://github.com/hostconfig/https.git).

Attempting to run Docker before generating these certificates per the instructions will likely cause the Docker build to fail, because the builder attempts to copy the certificates from your local disk (where you can use them further) instead of generating them inside of the Docker environment. A shell script named 'generate.sh' is provided which will create the required certificates in a new ```.certs/``` directory. As long as this is placed at the root of the 'https' sub-module, the Docker build should succeed. Please be vigilante about the useage of self-signed certificates; these are generally only to be used for local development purposes and should not be shared publically.

### Thanks for reading!

[Nathan J. Hood](https://github.com/nathanjhood)
