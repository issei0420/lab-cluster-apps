# Install Linkerd Viz

this also creates service monitor resource from monitoring.coreos.com/v1,
so that metrics scraped by the linkerd-viz prometheus can be exported to primary prometheus via federation API.

Install linkerd-viz chart
```sh
helm template linkerd-viz \
    -n linkerd-viz \
    linkerd/linkerd-viz \
    > manifests.yaml
```
