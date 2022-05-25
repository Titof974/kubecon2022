# From docker push to Bytes on Disk
*Presenters: Wayne Warren, Adam Wolfe Gordon*

## Content Addressable Object Store

Tags -> manifest (kind of pointers) -> blobs (layers)

## CNCF Distribution
[distribution/distribution](https://github.com/distribution/distribution)

## OCI Distribution Spec

[distribution-spec](https://github.com/opencontainers/distribution-spec)

Http API for Docker registry

## Distribution Specs
### Inside docker push
URL: `/v1/<name>/blobs/upload`
- 2 ways to push blobs
	- Monolithic bloc upload
	- Chunked blob upload

### Blob "mounting"
`POST /v2/<repository>/blobs/upload/?mount=<digest>&from=<other repo>`

### Pushing Manifests and Tags

`PUT /v2/<repository>/manifests/<reference>`

A reference can be a digest or a tag.

### Pulling Manifests

`GET /v2/<repository>/manifests/<reference>` 

### Check blob

`HEAD /v2/<repository>/blobs/<?>`

### Distribution
Distribution doesnt support atomic


