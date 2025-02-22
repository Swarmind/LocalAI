# OCI Test

This package contains tests for the OCI (Open Container Initiative) module.

## File structure

- pkg/oci/blob_test.go
- pkg/oci/image_test.go
- pkg/oci/oci_suite_test.go
- pkg/oci/ollama_test.go

## Summary

The package tests various functionalities of the OCI module, including fetching blobs from images, loading and evaluating OCI image templates, extracting OCI images to temporary directories, and pulling model files from remote sources.

## Code relations

The tests in this package rely on the `github.com/mudler/LocalAI/pkg/oci` package to interact with OCI images and the `github.com/onsi/ginkgo/v2` and `github.com/onsi/gomega` packages for testing purposes.

## Unclear places

None.

## Dead code

None.

## Edge cases

None.

