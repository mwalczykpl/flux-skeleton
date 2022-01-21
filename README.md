# Flux skeleton

Sekeleton for fluxcd GitOps repository for kubernetes cluster.

```shell
export GITHUB_TOKEN=ghp_XXXXXXXXXXXXXXXXXXXXX
export GITHUB_USER=username
```

```shell
flux bootstrap github \
--owner=$GITHUB_USER \
--repository=flux-skeleton \
--branch=master \
--path=clusters/development \
--personal
```

