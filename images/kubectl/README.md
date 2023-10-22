<!--monopod:start-->
# kubectl
| | |
| - | - |
| **OCI Reference** | **Version** |
| `public.ecr.aws/t4s8c0c3/kubectl:latest` | 1.28.3 |


---
<!--monopod:end-->

Minimal image with kubectl binary.

## Get It!

The image is available on `public.ecr.aws`:

```
docker pull public.ecr.aws/t4s8c0c3/kubectl
```

## Usage

`kubectl` is a minimal secure image with no shell. You can use the image as follows:

```

docker run public.ecr.aws/t4s8c0c3/kubectl:latest help

```

You will see the results:

```
kubectl controls the Kubernetes cluster manager.

 Find more information at: https://kubernetes.io/docs/reference/kubectl/

Basic Commands (Beginner):
  create          Create a resource from a file or from stdin
  expose          Take a replication controller, service, deployment or pod and expose it as a new Kubernetes service
  run             Run a particular image on the cluster
  set             Set specific features on objects

Basic Commands (Intermediate):
  explain         Get documentation for a resource
  get             Display one or many resources
  edit            Edit a resource on the server
  delete          Delete resources by file names, stdin, resources and names, or by resources and label selector
...

```

## Provenance

All Initializ Secure Images contain verifiable signatures and high-quality SBOMs (software bill of materials), features that enable users to confirm the origin of each image built and have a detailed list of everything that is packed within.

### Verifying Image Signatures 

The kubectl Initializ Secure Images are signed using Sigstore, and you can check the included signatures using cosign.

The following command requires [cosign](https://docs.sigstore.dev/cosign/overview/) and [jq](https://stedolan.github.io/jq/) to be installed on your machine. It will pull detailed information about all signatures found for the provided image.

```

cosign verify public.ecr.aws/t4s8c0c3/kubectl \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity https://github.com/initializ/secure-images/.github/workflows/release.yml@refs/heads/main | jq

```

By default, this command will fetch signatures for the latest tag. You can also specify the tag you'd like to fetch signatures for.

### Downloading and Verifying SBOMs 

All Initializ Secure Images come with a high-quality Software Bill Of Materials (SBOM) attested at build-time. The SBOM can be downloaded using the cosign tool:

```

cosign download attestation --predicate-type https://spdx.dev/Document \
  public.ecr.aws/t4s8c0c3/kubectl:latest | jq -r .payload | base64 -d | jq

```

This command will fetch the SBOM assigned to the latest tag by default. You can also specify the tag you'd like to fetch the SBOM from.

You can also use the cosign verify-attestation command to check the signature of an SBOM:

```

cosign verify-attestation public.ecr.aws/t4s8c0c3/kubectl \
  --type https://spdx.dev/Document --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity https://github.com/initializ/secure-images/.github/workflows/release.yml@refs/heads/main

```

And you should get output that verifies the SBOM signature in cosign’s transparency log:

```
Verification for public.ecr.aws/t4s8c0c3/kubectl --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The code-signing certificate was verified using trusted certificate authority certificates
Certificate subject: https://github.com/initializ/secure-images/.github/workflows/release.yml@refs/heads/main
Certificate issuer URL: https://token.actions.githubusercontent.com
GitHub Workflow Trigger: workflow_dispatch
GitHub Workflow SHA: b28dde272047fd4c0729343d14d5fd8d1af49192
GitHub Workflow Name: .github/workflows/release.yml
GitHub Workflow Repository: initializ/secure-images
GitHub Workflow Ref: refs/heads/main
...
```
