# Publishing

Be sure all **tests** pass!

```
$ bundle exec rake test
```

Also check the **linter**:

```
$ bundle exec rubocop
```

**Count** the number of hash type supported:

```
$ bundle exec rake count
```

Update the number in the following files:

- `README.md`
- `docs/_coverpage.md`
- `docs/README.md`
- `docs/why.md`

On new release don't forget to rebuild the **library documentation**:

```
$ bundle exec yard doc
```

Create an **annotated git tag**:

```
$ git tag -a vx.x.x
```

Push the changes including the tags:

```
$ git push --follow-tags
```

Build the **gem**:

```
$ gem build haiti.gemspec
# or
$ bundle exec rake build
```

Push the new gem release on **RubyGems** See https://guides.rubygems.org/publishing/.

```
$ gem push haiti-hash-x.x.x.gem
```

## Docker container registries

<!-- tabs:start -->

### **Docker Hub**

```
$ docker build -f Dockerfile -t noraj/haiti:x.x.x --build-arg HAITI_VERSION=x.x.x .

$ docker login docker.io

$ pass show docker-credential-helpers/aHR0cHM6Ly9pbmRleC5kb2NrZXIuaW8vdjEv/USERNAME
$ docker push docker.io/noraj/haiti:x.x.x
$ docker push docker.io/noraj/haiti
```

### **Github (GHCR)**

GHCR = Github Container Registry

```
$ docker build -f Dockerfile -t ghcr.io/noraj/haiti:x.x.x --build-arg HAITI_VERSION=x.x.x .

$ export CR_PAT=YOUR_TOKEN
$ echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin

$ pass show docker-credential-helpers/Z2hjci5pbw==/USERNAME
$ docker push ghcr.io/noraj/haiti:x.x.x
$ docker push ghcr.io/noraj/haiti
```

### **Alibaba Cloud (ACR)**

ACR = Alibaba Cloud Container Registry

```
$ docker build -f Dockerfile -t registry-intl.eu-central-1.aliyuncs.com/noraj/haiti:x.x.x --build-arg HAITI_VERSION=x.x.x .

$ docker login registry-intl.eu-central-1.aliyuncs.com

$ pass show docker-credential-helpers/cmVnaXN0cnktaW50bC5ldS1jZW50cmFsLTEuYWxpeXVuY3MuY29t/USERNAME
$ docker push registry-intl.eu-central-1.aliyuncs.com/noraj/haiti:x.x.x
$ docker push registry-intl.eu-central-1.aliyuncs.com/noraj/haiti
```

<!-- tabs:end -->
