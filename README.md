# Spring Native Demo

The best thing in the world for these tedious setups for native builds (e.g. on Windows with Visual Studio, always 1000 hacks because it doesn't work and all that stuff 🤬) are automated pipelines 🚀.

Download the build artifacts in the `Artifacts` section under https://github.com/jzelAdmin2006/spring-native-demo/actions/runs/<build-xyz\>.

Another blessing is the Docker buildx feature, which allows you to build multi-arch images with a single command. This is a great way to build images for different platforms with a single command.

```sh
docker buildx build --platform linux/amd64,linux/arm64 -f Dockerfile-standalone.native-micro -t jzeladmin2006/spring-native-demo --push .
```
