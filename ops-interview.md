## Background
[What is Platform Engineer ?](https://softwareengineeringdaily.com/2020/02/13/setting-the-stage-for-platform-engineering/)

## Ops / Devop Engineering

### Experiences:

- Understanding of cloud-native architectures like 12-factor apps
- Working experiences with K8 and/or CloudFoundry(CF). If CF knowledge is lacking, read it up and able to elaborate pros and cons
- Strong experiences in using AWS services
- Strong in Linux and development skills on automation, eg: shell/make/python script. Experience in what it means as by Dev/OPs as code. Knowledge on terraform or ansible is a plus
- Strong knowledge on how to leverage docker/dockerfiles for automation.
- Strong knowledge how to leverage and use CI/CD tools like Jenkins/Jenkinsfile

### Screening exercise for interview

1. Execute full stack engineer setup exercise locally – ie: [README-DevEnv.MD](https://github.com/gitricko/nameko-devex/blob/master/README-DevEnv.md). 
    1. How does this framework support micro-services architecturally?
    2. What are the alternatives ? What are the pros and cons
2. Install/Automate [Epinio](https://docs.epinio.io/installation/install_epinio) (locally with docker/k3d with IP_ADDR.sslip.io as system domain)
    1. Understand what is framework is trying to abstract out? Does it make thing easier for developers/operator by using epinio vs native K8
3. Execute [README-DevOps.md](https://github.com/gitricko/nameko-devex/blob/master/README-DevOps.md) but on [Epinio](https://github.com/epinio/epinio)
    1. What are the pros/cons for develops, operators, security etc 