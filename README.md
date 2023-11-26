# Stable Diffusion on Kubernetes with Helm

**NOTE: This fork is an updated version of [amithkk/stable-diffusion-k8s](https://github.com/amithkk/stable-diffusion-k8s) that uses the latest (as at 26 November 2023) Stable Diffusion web UI image and comes with more models than the previous version.** This fork does not build a custom image, but rather uses the latest version of the `tukirito/sygil-webui` image.

Run Stable Diffusion with companion models on a GPU-enabled Kubernetes Cluster - complete with the updated [StreamLit WebUI](https://github.com/Sygil-Dev/sygil-webui) and automatic model fetching for a 2 step install that takes less than 2 minutes (excluding download times).

Uses the already-configured `tukirito/sygil-webui` image.

![Screenshot of the Stable Diffusion UI](img/screenshot.png)

### Features

-   Automatic Model Fetching
-   Works with `gpu-operator`, bundling CUDA libraries
-   Interactive UI with many features, and more on the way!
-   GFPGAN for face reconstruction, RealESRGAN for super-sampling.
-   [Textual Inversion](https://github.com/hlky/sd-enable-textual-inversion)
-   many more!

### Prerequisites

-   Kubernetes Cluster with GPUs attached to atleast one node, and [NVIDIA's `gpu-operator`](https://github.com/NVIDIA/gpu-operator) set up successfully
-   [`helm`](https://helm.sh/docs/intro/install/) installed locally

## Setup

-   Add the helm repo with `helm repo add matemalice-sd https://matemalice.github.io/stable-diffusion-k8s`
-   Fetch latest charts with `helm repo update`
-   (Optional) Create your own [`values.yaml`](./charts/stable-diffusion/values.yaml) with customized settings
    -   Some things that you might want to change could include the `nodeAffinity`, `cliArgs` (see below) and `ingress` settings (that will allow you to access this externally without needing to `kubectl port-forward`)
-   Install with `helm install --generate-name amithkk-sd/stable-diffusion -f <your-values.yaml>`

Wait for the containers to come up and follow the instructions returned by Helm to connect. This may take a while as it has to download a ~5GiB docker image and ~5GiB of models

# Config

Configuration options can be specified in `values.yaml`.

# Disclaimer

The author(s) of this project are not responsible for any content generated using this interface.

# Thanks

Special thanks to everyone behind these awesome projects, without them, none of this would have been possible:

-   [StreamLit WebUI](https://github.com/Sygil-Dev/sygil-webui)
-   [amithkk/stable-diffusion-k8s](https://github.com/amithkk/stable-diffusion-k8s)
-   [hlky/stable-diffusion-webui](https://github.com/hlky/stable-diffusion-webui)
-   [AbdBarho/stable-diffusion-webui-docker](https://github.com/AbdBarho/stable-diffusion-webui-docker/)
-   [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)
-   [CompVis/stable-diffusion](https://github.com/CompVis/stable-diffusion)
