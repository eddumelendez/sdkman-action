# SDKMAN! action

This action installs any `candidate` via [sdkman](https://sdkman.io/). If inputs are provided then the 
`sdk install <candidate> <version>` command will be executed. Otherwise, the `sdk env install` command will be executed.

## Inputs

### `candidate`

**Optional** The name of the candidate to install.

### `version`

**Optional** The version of the candidate to install.

## Outputs

### `file`

Filename of the downloaded archive.

## Example usage

Install a specific candidate in using Windows runner:

```yaml
- uses: sdkman/sdkman-action@master
  id: sdkman
  with:
    candidate: java
    version: 15.0.0-amzn
- uses: actions/setup-java@v1
    id: setup-java
    with:
      java-version: 15.0.0
      jdkFile: ${{ steps.sdkman.outputs.file }}
- run: java --version
```

Install a specific candidate in Linux or macOS runner:

```yaml
- uses: sdkman/sdkman-action@master
  id: sdkman
  with:
    candidate: java
    version: 15.0.0-amzn
- run: java --version
```

Install candidates from `.sdkmanrc` in Linux or macOS runner:

```yaml
- uses: sdkman/sdkman-action@master
  id: sdkman
- run: java --version
```
