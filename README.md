# Fluxcd skeleton

Sekeleton for fluxcd GitOps repository for kubernetes cluster.
Code is splited into apps and infrastructure and prepared for two environments development and production. 

Sample application consist of frontend and backend base on nginx image. Infrastructure deliver MariaDB database with default settings.

## Requirements
- First make a copy of all files and place them into you repository,
- Install fluxcd into your system (https://fluxcd.io/docs/installation/),
- optionally if you don't have it already deploy Kubernet,es cluster, use Docker and Kind to create example cluster (https://kind.sigs.k8s.io/docs/user/quick-start/),
- generate github token in GH your account settings

## Deployment
For a time of bootstrap export variables GITHUB_TOKEN and GITHUB_USER,
```shell
export GITHUB_TOKEN=ghp_XXXXXXXXXXXXXXXXXXXXX
export GITHUB_USER=username
```

Bootstrap flux into your cluster, please see `flux --help` for more options:

```shell
flux bootstrap github \
--owner=$GITHUB_USER \
--repository=flux-skeleton \
--branch=master \
--path=clusters/development \
--personal
```

Now you should see kustomizations ready like below:
```shell
mariusz  kubectl -n flux-system get kustomizations
NAME             READY   STATUS                                                              AGE
apps             True    Applied revision: master/81a52c81155fc254863df514edbd7b8d939f0c84   104m
flux-system      True    Applied revision: master/81a52c81155fc254863df514edbd7b8d939f0c84   106m
infrastructure   True    Applied revision: master/81a52c81155fc254863df514edbd7b8d939f0c84   104m
```

Tt's a time to update project with your custom resources, keep your application resoureces in app/base/<application-name> and infrastructure (like databases, ingress) in infrastructure/base/<infrastrucure-resource> folder.


Enjoy :)
