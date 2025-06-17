# Today I learned

###  How to authenticate podman with Google Artifact Registry

Google Cloud has good documentation, even a special command, on how to authenticate Docker with the Google Cloud Artifact Registry (`gcloud auth configure-docker`). The solution for [podman](https://podman.io/) was less accessible, but this is a way that to do it (it also works with docker).
```sh
gcloud auth print-access-token | podman login -u oauth2accesstoken --password-stdin https://europe-north1-docker.pkg.dev
podman push europe-north1-docker.pkg.dev/myimage:mytag
```
I use the GCP region europe-north1, you need to choose what is appropriate for you. 
Replace `<region>` with your registry's region (e.g., `us`, `europe`, etc.).

gcloud auth print-access-token gives a token that lasts for 1 hour.
