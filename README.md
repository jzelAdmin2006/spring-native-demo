# Spring Native Demo

The best thing in the world for these tedious setups for native builds (e.g. on Windows with Visual Studio, always 1000 hacks because it doesn't work and all that stuff 🤬) are automated pipelines 🚀.

Download the build artifacts in the `Artifacts` section under https://github.com/jzelAdmin2006/spring-native-demo/actions/runs/<build-xyz\>.

Another blessing is the Docker buildx feature, which allows you to build multi-arch images with a single command.

```sh
docker buildx build --platform linux/amd64,linux/arm64 -f Dockerfile-standalone.native-micro -t jzeladmin2006/spring-native-demo --push .
```

Docker Images Overview

- native-micro: Built from a statically linked Musl binary. This makes it extremely lightweight, with fast startup times, optimized for horizontal scaling.
- native: Uses Alpine to allow inspection, since it includes a shell and standard utilities.
- native-glibc: Provides a Glibc-based binary. This is primarily included for demonstration purposes in this repository. In practice, you might release a Glibc binary directly, in which case using a different binary (e.g. statically linked Musl) for the Docker image can be considered overkill. Glibc offers some advantages compared to Musl such as better hardware-level optimizations, is however somewhat heavier.
- native-glibc-debug: Uses the debug variant of the distroless base image. This image follows the same principle as the Alpine-based image but is intended strictly for debugging. Unlike Alpine, distroless:debug is not meant for deployment as the name suggests.
- jvm: Runs the application's JAR in an Alpine JRE. Startup time is naturally longer, but throughput can be higher, since the JVM can optimize performance during runtime.
