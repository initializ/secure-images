# Initializ Secure Images
Initializ Secure Images is a collection of container images designed for security. 

All these images are built using [apko](https://github.com/chainguard-dev/apko) and [melange](https://github.com/chainguard-dev/melange). These tools provide a reproducible, declarative approach to building OCI images.

## Find and use Initializ Secure Images

Our images are available via public.ecr.aws.

For example, to pull the `kubectl` image with Docker:

```
docker pull public.ecr.aws/t4s8c0c3/kubectl:latest
```

### Software and Tools

These images contain stand-alone software, such as databases and web servers, and tools like `kubectl` and `aws-cli`.

Because our images are constantly rebuilt with the latest sources and include the absolute minimum of dependencies, they typically have significantly fewer vulnerabilities than equivalent images.

For example:
 - [kubectl](https://github.com/initializ/secure-images/tree/main/images/kubectl) 
 - [git](https://github.com/initializ/secure-images/tree/main/images/git)
 - [aws-cli](https://github.com/initializ/secure-images/tree/main/images/aws-cli)

## Signatures

All Initializ Secure Images are signed using [Sigstore](https://www.sigstore.dev/), and you can check the signature using [`cosign`](https://docs.sigstore.dev/cosign/overview). For our `kubectl` image example, you can run the following:

```
cosign verify public.ecr.aws/t4s8c0c3/kubectl --certificate-oidc-issuer https://token.actions.githubusercontent.com --certificate-identity https://github.com/initializ/secure-images/.github/workflows/release.yml@refs/heads/main | jq 
```

Your output will make sure that the cosign claims are validated.

## SBOMs

All Initializ Secure Images come with a [Software Bill Of Materials (SBOM)](https://www.initializ.ai/blog/software-bill-of-materials-sbom-a-comprehensive-guide) generated at build-time. The SBOM can be downloaded using the [`cosign`](https://docs.sigstore.dev/cosign/overview) tool e.g.:

```
$ cosign download attestation --predicate-type https://spdx.dev/Document public.ecr.aws/t4s8c0c3/kubectl | jq -r .payload | base64 -d | jq
{
{
  "_type": "https://in-toto.io/Statement/v0.1",
  "predicateType": "https://spdx.dev/Document",
  "subject": [
    {
      "name": "public.ecr.aws/t4s8c0c3/kubectl",
      "digest": {
        "sha256": "6f932665bebaa373c5eb3bb150222137e6037142f238f06f464237ef26211778"
      }
    }
  ],
  "predicate": {
    "SPDXID": "SPDXRef-DOCUMENT",
    "creationInfo": {
      "created": "2023-10-18T18:17:54Z",
      "creators": [
        "Tool: apko (c419221)",
        "Organization: Chainguard, Inc"
      ],
      "licenseListVersion": "3.16"
    },
    "dataLicense": "CC0-1.0",
    "documentDescribes": [
      "SPDXRef-Package-sha256-9bf86620a4ea8a1ec0a6cc3501ef415daf6bbf4d7e7257a0749cddd9cd20a187"
    ],
    "documentNamespace": "https://spdx.org/spdxdocs/apko/",
    "files": [
  ...
```
