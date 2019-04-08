# Deploy apps to Kubernetes with no YAML files 😱

Using [Cloud Native Buildpacks](https://buildpacks.io) and
[Spring Boot Helm starter](https://github.com/alexandreroman/spring-boot-helm-starter)
you can **deploy a Spring Boot app to Kubernetes with no Dockerfile and no YAML files!**

<img src="https://i.imgur.com/gZN0r7r.gif"/>

## How to use it?

Compile this app using JDK 8:
```bash
$ ./mvnw clean package
```

Create a Docker image using [Cloud Native Buildpacks](https://buildpacks.io)
(you don't need a Dockerfile!):
```bash
$ pack build myrepo/noyaml --publish
```

Make sure to install
[Spring Boot Helm starter](https://github.com/alexandreroman/spring-boot-helm-starter)
to generate Kubernetes descriptors.

Generate Kubernetes descriptors using Helm:
```bash
$ helm create --starter=spring-boot noyaml
```

Edit generated file `noyaml/values.yml` and set your Docker image:
```yaml
image:
  repository: myrepo/noyaml
```

You are now ready to deploy this app using Helm:
```bash
$ helm install --namespace noyaml noyaml
```

## Contribute

Contributions are always welcome!

Feel free to open issues & send PR.

## License

Copyright &copy; 2019 [Pivotal Software, Inc](https://pivotal.io).

This project is licensed under the [Apache Software License version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
