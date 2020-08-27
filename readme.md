# Container Image with illegal char in version problem

When using a illegal character in the version the build fails, which is ok.
e.g.:
```groovy
// version that contains a '+'
version="1.6.0-dev.2.uncommitted+wip.foo.c75795d"
```
**But** when used in combination with a customer image name like for example: 

```groovy
tasks.named("bootBuildImage") {
    imageName = "registry.example.com/example/example-app:${version}"
}
```

The `bootBuildImage` does neither fails nor complete but runs forever.
