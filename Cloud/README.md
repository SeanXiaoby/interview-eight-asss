# Cloud Software Engineer

---

## Basic Cloud Knowledge

- [ ] [Cloud Computing](#cloud-computing)
- [ ] [Cloud Services](#cloud-services)
- [ ] [Public, Private, and Hybrid Clouds](#public-private-and-hybrid-clouds)
- [ ] [Cloud Service Scalability](#cloud-service-scalability)

### Cloud services types

- **IaaS** (Infrastructure as a Service): rent virtual machines, storage, load balancers, etc.
- **PaaS** (Platform as a Service): rent a platform to deploy your applications on (e.g. Heroku, Google App Engine, etc.)
- **SaaS** (Software as a Service): rent a software (e.g. Gmail, Dropbox, etc.)

### Key Cloud services

- Cloud computing (EC2, GCE, etc.)
- Storage (S3, Google Cloud Storage, etc.)
- Database (RDS, Cloud SQL, etc.)
- Networking (VPC, Cloud DNS, etc.)
- Big Data (BigQuery, Cloud Datastore, etc.)
- Machine Learning (Cloud ML Engine, etc.)

### Public, Private, and Hybrid Clouds:

- **Public Cloud**: Cloud services offered over the public Internet and available to anyone who wants to purchase the service.
- **Private Cloud**: Cloud services offered over a private internal network and available only to internal users.
- **Hybrid Cloud**: A combination of public and private cloud services.

### Cloud service scalability

- **Vertical scaling**: increasing the capacity of a single machine (e.g. adding more RAM, CPU, etc.)
- **Horizontal scaling**: increasing the number of machines (e.g. adding more machines to the pool of available machines)
- **Elasticity**: the ability to scale up and down (e.g. adding more machines when the load increases and removing machines when the load decreases)
- **Autoscaling**: the ability to automatically scale up and down based on the load (e.g. adding more machines when the load increases and removing machines when the load decreases)
- **Load Balancing**: distributing the load across multiple machines (e.g. distributing the load across multiple machines)
- **Serverless**: a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers. A serverless application runs in stateless compute containers that are event-triggered, ephemeral (may last for one invocation), and fully managed by the cloud provider.

---

## Docker and Docker Orchestration

- [ ] [Docker](#docker)
- [ ] [Docker Orchestration](#docker-orchestration)

### Docker

- [ ] [Docker](https://www.docker.com/)

#### Dockerfile

To deploy a nodejs backend service in a docker container, we need to create a `Dockerfile` in the root directory of the project.

```dockerfile
# Use the official image as a parent image.
FROM node:current-slim

# Set the working directory.
WORKDIR /usr/src/app

# Copy the source codes into the container.
COPY . .

# Run the command inside your image filesystem.
RUN npm install

# Inform Docker that the container is listening on the specified port at runtime.
EXPOSE 8080

# Run the specified command within the container.
CMD [ "npm", "start" ]
```

#### Upload/pull docker image

```bash
# Upload docker image to docker hub
docker push <dockerhub_username>/<dockerhub_repository>:<tag>

# Pull docker image from docker hub
docker pull <dockerhub_username>/<dockerhub_repository>:<tag>
```

#### Run multiple containers

Let's say we have three services to run:
- `Nodejs` backend service
- `MongoDB` database service
- `Redis` cache service

We can use `docker-compose` to run all three services in one command. And we also have to define the dockerfile for each service.

```yaml
version: '3'
services:
    mongodb:
        image: mongo:latest
        container_name: my-mongodb
        ports:
            - "27017:27017"

    nodejs-backend:
        build:
            context: .  # Use the current directory as the build context
            dockerfile: ./backend/Dockerfile  # Specify the Dockerfile path
        container_name: my-nodejs-backend
        ports:
            - "3000:3000"
        depends_on:
            - mongodb  # Specify the dependency, make sure the MongoDB service is started before the Node.js backend service

    redis:
        image: redis:latest
        container_name: my-redis
        ports:
            - "6379:6379"
```

To run the services, we can use the following command:

```bash
docker-compose up
```

### Docker Orchestration

- [ ] [Kubernetes](https://kubernetes.io/)

#### Kubernetes

- Pods : A pod is a group of one or more containers (such as Docker containers), with shared storage/network, and a specification for how to run the containers.
- Services : An abstract way to expose an application running on a set of Pods as a network service.
- Deployments : A Deployment provides declarative updates for Pods and ReplicaSets.
- ReplicaSets : A ReplicaSet ensures that a specified number of pod replicas are running at any given time.
- Nodes : A node is a worker machine in Kubernetes, previously known as a minion. A node may be a VM or physical machine, depending on the cluster.

#### Deploy a cluster on AWS

- Create a cluster on AWS using [eksctl](https://eksctl.io/)

```bash
eksctl create cluster \
--name <cluster_name> \
--version 1.17 \
--region <region> \
--nodegroup-name <nodegroup_name> \
--node-type t2.micro \
--nodes 2 \
--nodes-min 1 \
--nodes-max 3 \
--managed
```

- Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

```bash
# Install kubectl on macOS
brew install kubectl

# Download the latest release with the command:
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

# Make the kubectl binary executable.
chmod +x ./kubectl

# Move the binary in to your PATH.
sudo mv ./kubectl /usr/local/bin/kubectl
```

- Configure kubectl

```bash
aws eks --region <region> update-kubeconfig --name <cluster_name>
```

- Deploy a sample application

```bash
kubectl apply -f https://k8s.io/examples/application/deployment.yaml
```

