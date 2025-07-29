# Update OpenAPI Specification Version

A custom GitHub Action that updates the version and server URL in an OpenAPI specification file.

This action locates the first *.openapi.yml file in the given path, updates its info.version field, and rewrites the first servers[0].url using a standard SwaggerHub format. 
It is designed for CI pipelines that require versioned OpenAPI definitions as part of their build or release process.

## Example Usage

```yaml
jobs:
  version-openapi:
    runs-on: ubuntu-latest
    permissions:
      id-token: write
      attestations: write
    steps:
      - uses: actions/checkout@v4

      - name: Update OpenAPI spec
        uses: hmcts/update-openapi-version@main
        with:
          openapi_path: ./src/main/resources/openapi
          api_name: the-api-name
          api_version: version-of-api
```

**NOTE:** The permissions section is required as it uses [actions/attest-build-provenance](https://github.com/marketplace/actions/attest-build-provenance)
after updating the OpenAPI spec artefact.
```yaml
permissions:
      id-token: write
      attestations: write
```

## License

This project is licensed under the [MIT License](LICENSE).
