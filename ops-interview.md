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
    
    Answers:
      - Conda creates environment favourable to nameko-devex and the full stack is created in this environment
      - Products, orders and gateway services are seperate docker containers connected with RabbitMQ which takes the advantage of loose coupling instead of a Monolithic architecture.
      - It opens different ports in host(8000,8001,8002,8003), which makes troubleshooting and fixing easier
      - Smoke testing is using localhost:8000 and unit testing uses code coverage with pytest on different containers(products,orders and gateway)
      

    2. What are the alternatives ? What are the pros and cons
   
    Answers:
      - We can use Monilithic Architecture ==> pro - good for legacy applications | con - very difficult to manage as its tighly coupled
      - Use multi-cluster kubernetes with helm ==> pro - Easy deployment of apps | con - Need to manage K8S infra and difficult to setup infra
      - Use Cloud with manual deployment of each application with Jenkins ==> pro - Autoscaling and easy deployment | con - Need to manage Infra
    
2. Install/Automate [Epinio](https://docs.epinio.io/installation/install_epinio) (locally with docker/k3d with IP_ADDR.sslip.io as system domain)
    1. Understand what this framework is trying to abstract out? Does it make thing easier for developers/operator by using epinio vs native K8

Answers:
-  Epinio is a Kubernetes-powered application development engine and uses Epinio CLI to deploy to kubernetes.
-  In current exercise, product, order and gateway components are docker images, it can be easily deployed to kubernetes. 

yes it is easy for Developers/Operators using Epinio
-  Epinio is installed from a single Helm chart and makes easy for developers/operators to see live instance of their system which is accessible at a URL
-  Epinio needs Ingress-controller (nginx or traefik) for exposing application to URL in production
-  Also needs cert-manager to acquire TLS certificates for the apps
-  Epinio allows Developers to push code straight to the platform and it inspects the source, selects an appropriate buildpack and creates Kubernetes objects to deploy the app


3. Execute [README-DevOps.md](https://github.com/gitricko/nameko-devex/blob/master/README-DevOps.md) but on [Epinio](https://github.com/epinio/epinio)
    1. What are the pros/cons for develops, operators, security etc
     
Answers:

Pros-

 Developers:
-  Developers can concentrate on developing their application/business logic and build own images and store in repository or use Paketo Buildpack.
-  Advantage of using Epinio is once Epinio has been installed, no further Kubernetes knowledge is needed for developers.
-  Epinio is adding the needed abstractions and intelligence to allow Developers to use Kubernetes as a PaaS (Platform as a Service).
-  It’s quick to set up, simple to use and suitable for all environments

 Operators:
-  Because Epinio runs within your own Kubernetes cluster, Operators can interact directly with Kubernetes to monitor running apps, optimize cluster performance and act on problems.
-  They can decide how the cluster is set up (including how Epinio is installed) and how application should be deployed
-  Epinio eliminates the need of CI/CD pipelines which make the job of Operators easier

 Security:
-  Epinio is secured with self signed and CA certificates
-  As container images are saved in private repo, its secured

Cons-

- Difficult to manage backend Kubernetes cluster( upgrade of K8s internal components)
- Self Signed and CA certificates need to be validated and renewed
