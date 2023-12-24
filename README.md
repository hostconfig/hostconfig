# hostconfig
Welcome to hostconfig.

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

```
$ docker compose up --build

building 0...100%

http server listening on http://localhost:8080
https server listening on https://localhost:443

$ docker compose down
```

*NOTE:* the 'https' module requires an additional build step to generate the required self-signed TLS certificates, which must also be installed in your browser and/or client - [full instructions are available in the project repository](https://github.com/hostconfig/https.git).

More services and content can be easily added to the 'src' directory, such as a database server and api routes (coming soon).

Thanks for reading!

[Nathan](https://github.com/nathanjhood)
