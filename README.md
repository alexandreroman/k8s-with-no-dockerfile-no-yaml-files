# Hello World with Spring Cloud Kubernetes

This project shows how to use
[Spring Cloud Kubernetes](https://spring.io/projects/spring-cloud-kubernetes)
to run Spring Boot apps in a Kubernetes cluster.

## How to use it?

Compile this app using JDK 8:
```bash
$ ./mvnw clean package
```

Create a Docker image using [Cloud Native Buildpacks](https://buildpacks.io)
(you don't need a Dockerfile!):
```bash
$ pack build myrepo/hello-sck --publish
```

Make sure to install
[Spring Boot Helm starter](https://github.com/alexandreroman/spring-boot-helm-starter)
to generate Kubernetes descriptors.

Generate Kubernetes descriptors using Helm:
```bash
$ helm create --starter=spring-boot hello-sck
```

Edit generated file `hello-sck/values.yml` and set your Docker image:
```yaml
image:
  repository: myrepo/hello-sck
```

You are now ready to deploy this app using Helm:
```bash
$ helm install --namespace hello-sck hello-sck
```

## Contribute

Contributions are always welcome!

Feel free to open issues & send PR.

## License

Copyright &copy; 2019 [Pivotal Software, Inc](https://pivotal.io).

This project is licensed under the [Apache Software License version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
