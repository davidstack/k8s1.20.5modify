### conformance

`conformance` is a standalone container to launch Kubernetes end-to-end tests, for the purposes of conformance testing.
`conformance` is built for multiple architectures and _the image is pushed automatically on every release._

#### How to release by hand

```console
# First, build the binaries by running make from the root directory
$ make WHAT="test/e2e/e2e.test vendor/github.com/onsi/ginkgo/ginkgo cmd/kubectl cluster/images/conformance/go-runner"

# Build for linux/amd64 (default)
# export REGISTRY=$HOST/$ORG to switch from registry.cn-hangzhou.aliyuncs.com/google_containers

$ make push VERSION={target_version} ARCH=amd64
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance-amd64:VERSION
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance:VERSION (image with backwards-compatible naming)

$ make push VERSION={target_version} ARCH=arm
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance-arm:VERSION

$ make push VERSION={target_version} ARCH=arm64
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance-arm64:VERSION

$ make push VERSION={target_version} ARCH=ppc64le
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance-ppc64le:VERSION

$ make push VERSION={target_version} ARCH=s390x
# ---> registry.cn-hangzhou.aliyuncs.com/google_containers/conformance-s390x:VERSION
```

If you don't want to push the images, run `make` or `make build` instead


#### How to run tests

```
kubectl create -f conformance-e2e.yaml
```

[![Analytics](https://kubernetes-site.appspot.com/UA-36037335-10/GitHub/cluster/images/conformance/README.md?pixel)]()
