# Wercker [godep][1] box [![wercker status](https://app.wercker.com/status/5b8737d411d017d8a11701d74d9874da/s "wercker status")](https://app.wercker.com/project/bykey/5b8737d411d017d8a11701d74d9874da)

Box that extends the default wercker/golang box to include godep for faster
builds.


## Usage

Just add this to your `wercker.yml`:

```yaml
box: attilaolah/godep
```

This will execute the default build steps (see below), but you can customise
these steps too:

```yaml
box: attilaolah/godep
# Build definition
build:
  # The steps that will be executed on build
  steps:
    # Sets the go workspace and places you package
    # at the right place in the workspace tree
    - setup-go-workspace

    # Build the project
    - script:
        name: godep go build
        code: |
          godep go build ./...

    # Test the project
    - script:
        name: godep go test
        code: |
          godep go test ./...
```


## Versioning

The current version is **1.107.3**.

The major version will remain at 1. The minor version (currently 107) will
increase as [godep][2] itself is updated. The patch (or bug-fix) will be zero
unless I need to change something in the box itself without updating godep (for
example, updating the platform the box runs on).

You can pin to a specific version like this:

```yaml
box: attilaolah/godep@1.107.3
```

[1]: //app.wercker.com/#applications/547330e6a60c33c27c279f8e/tab/details
[2]: //github.com/tools/godep
