# ============================================================
# COMPLETE DEVOPS & CLOUD INTERVIEW PREPARATION GUIDE
# Beginner to Senior Level | All Topics Covered
# For: Senior Software Engineer Interviews
# ============================================================

---

# PART 1 — GIT & GITHUB

## What is Git?
Git is like a "save button" for your code — but 100x smarter.
It remembers EVERY change you made, WHEN you made it, and WHO made it.

**Why used:** Track every code change, work with teams, go back to any previous version.

**Real-world example:** You write a story (code). You save version 1, 2, 3. Later you realize version 2 was better — Git lets you go back!

---

## Core Git Concepts

### Repository (Repo)
A folder that Git is tracking.
```bash
git init          # make folder into git repo
git clone URL     # copy someone else's repo
```

### Commit — A snapshot of your code at a point in time
```bash
git add .                    # stage all changes
git commit -m "fix login bug" # save snapshot
```

### Push & Pull
```bash
git push   # upload commits to GitHub
git pull   # download latest commits from GitHub
```

### Branch — A parallel version of your code
```bash
git checkout -b feature-login  # create + switch to branch
git checkout main              # go back to main
```

### Merge — Combine two branches
```bash
git checkout main
git merge feature-login
```

### Rebase — Move your commits on top of another branch
```bash
git rebase main   # rebase current branch on main
```
**Merge vs Rebase:**
- Merge → keeps full history, creates merge commit
- Rebase → cleaner linear history, rewrites commits

### Cherry-pick — Take ONE specific commit from another branch
```bash
git cherry-pick abc1234
```

### Stash — Temporarily save work without committing
```bash
git stash      # save changes temporarily
git stash pop  # bring them back
```

### HEAD — Where you are right now in Git history
**Detached HEAD:** HEAD points to a commit instead of a branch.
```bash
git checkout abc1234  # detached HEAD
git checkout main     # back to normal
```

### Tags — Permanent label for a commit (releases)
```bash
git tag v1.0.0
git push origin v1.0.0
```

### .gitignore — Tell Git which files to NEVER track
```
node_modules/
.env
*.log
```

### Git Hooks — Scripts that run automatically on Git events
Used for: run tests before commit, lint code, send notifications.

---

## Git Branching Strategies

### GitFlow (most common in companies)
```
main        → production-ready code
develop     → integration branch
feature/*   → new features
release/*   → preparing for release
hotfix/*    → emergency production fixes
```

### Trunk-Based Development
Only ONE main branch. Small, frequent commits. Feature flags for incomplete features.

### Feature Branch Strategy
Each feature = its own branch. Merge via Pull Request.

---

## Pull Request (PR) & Code Review

**Flow:**
1. Developer creates feature branch
2. Writes code, pushes to GitHub
3. Opens Pull Request
4. Team reviews code (Code Review)
5. Approved → merged to main

**Why code review?** Catch bugs before production, share knowledge, maintain quality.

---

## Merge Conflicts

Happens when two people edited the SAME line of code.
```
<<<<<<< HEAD (your version)
name = "Alice"
=======
name = "Bob"
>>>>>>> feature-branch
```
Fix: decide which version to keep, delete conflict markers, commit.

---

## Git Interview Questions & Answers

**Q: git pull vs git fetch?**
A: git fetch downloads but doesn't apply. git pull = fetch + merge.

**Q: What is git rebase?**
A: Moves your commits to start from latest main. Use for clean linear history. Don't use on shared branches.

**Q: What is detached HEAD?**
A: HEAD points to a commit, not a branch. Commits here are "lost" unless you create a branch.

**Q: Explain GitFlow.**
A: main=production, develop=integration, feature branches for new work, release for preparing, hotfix for emergency fixes.

**Q: How do you handle merge conflicts?**
A: Manually edit file, choose correct code, delete markers, git add, git commit.

**Q: Merge vs Rebase?**
A: Merge creates merge commit, keeps full history. Rebase rewrites history to be linear.

---

## Git Best Practices
- Small, frequent commits with meaningful messages
- Always work on a branch, never commit to main directly
- Never commit .env files or secrets
- Use .gitignore properly
- Keep branches short-lived

## Memory Trick
```
Git = Camera (takes snapshots of code)
GitHub = Photo Album stored online
Branch = Parallel universe of your code
Merge = Combine two universes
Commit = One snapshot
Push = Upload to album
Pull = Download latest photos
```

---

# PART 2 — DOCKER

## What is Docker?
Docker packages your app and EVERYTHING it needs (code, libraries, settings) into a neat box called a **Container**.

**Why Docker?**
Before: "It works on my computer but not yours!" — different OS, different libraries.
After: Everything needed is INSIDE the container. Same container runs anywhere.

---

## VM vs Docker

```
VIRTUAL MACHINE:
[App A] [App B] [App C]
[Guest OS] [Guest OS] [Guest OS]
[Hypervisor]
[Host OS]

DOCKER:
[App A] [App B] [App C]
[Docker Engine]
[Host OS]  ← containers SHARE this
```

| Feature    | VM                  | Docker            |
|-----------|---------------------|-------------------|
| Size       | GBs (full OS)       | MBs (shares OS)   |
| Startup    | Minutes             | Seconds           |
| Isolation  | Strong (own OS)     | Process-level     |
| Performance| Slower              | Near-native       |

---

## Core Docker Concepts

### Image — Blueprint for a container
```bash
docker images              # list images
docker pull nginx          # download image
docker build -t myapp .    # build from Dockerfile
```

### Container — A running instance of an image
```bash
docker run nginx           # create + start
docker ps                  # list running containers
docker stop <id>           # stop container
docker rm <id>             # delete container
```

### Dockerfile — Instructions to build an image
```dockerfile
FROM node:18
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```
Each line = one layer. Layers are CACHED (fast rebuilds).

### Docker Compose — Run multiple containers together
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: secret
```
```bash
docker-compose up    # start all
docker-compose down  # stop all
```

### Volumes — Persistent storage
Containers are temporary — data lost when deleted. Volumes save data permanently.
```bash
docker run -v /host/path:/container/path nginx
```

### Port Mapping
```bash
docker run -p 8080:3000 myapp
# host:8080 → container:3000
```

### Environment Variables
```bash
docker run -e DB_URL=postgres://... myapp
```

---

## Multi-Stage Build — Smaller production images
```dockerfile
# Stage 1: Build
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2: Production (only copy built files)
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/dist .
CMD ["node", "index.js"]
```
Result: Final image is MUCH smaller (no build tools or dev dependencies).

---

## Docker Architecture
```
Docker CLI → Docker Daemon (dockerd) → Container Runtime
                                       |          |
                                  Container1  Container2
```

**Docker Registry:** Storage for images.
- Docker Hub = public registry
- ECR = AWS private registry

---

## Container Lifecycle
```
Created → Running → Paused → Stopped → Deleted
```

---

## Docker Security Best Practices
- Never run as root (add USER directive)
- Use minimal base images (alpine)
- Scan images for vulnerabilities (trivy)
- Never store secrets in Dockerfile
- Use .dockerignore

---

## Docker Interview Questions & Answers

**Q: Image vs Container?**
A: Image = blueprint (static). Container = running instance (dynamic). One image → many containers.

**Q: What is a Dockerfile?**
A: Text file with step-by-step instructions to build a Docker image. Each instruction = one layer.

**Q: What are Docker volumes?**
A: Containers are stateless — data lost when deleted. Volumes provide persistent storage outside the container.

**Q: What is Docker Compose?**
A: Tool to define and run multi-container apps using YAML. E.g., app + database + redis together.

**Q: What is multi-stage build?**
A: Multiple FROM statements. Build in one stage, copy only needed files to final stage. Much smaller images.

**Q: VM vs Docker?**
A: VMs include full OS (GBs, slow). Docker shares host OS (MBs, fast). Docker is lighter and faster.

---

## Memory Trick
```
Docker = Shipping container for software
Dockerfile = Recipe to build the container
Image = Pre-packed container (not running)
Container = Running, opened container
Volume = External hard drive
Compose = Manager of multiple containers
Registry = Warehouse to store containers
```

---

# PART 3 — MICROSERVICES

## What are Microservices?
Break one BIG app into MANY SMALL independent services.
Each service does ONE thing only and can be deployed separately.

**Analogy:** Restaurant with specialized stations — one chef ONLY makes pizza, one ONLY salad. If salad chef is sick, pizza still works!

---

## Monolith vs Microservices

```
MONOLITH: [Auth + Products + Orders + Payments + Notifications]
All in ONE codebase, ONE database, ONE deployment

MICROSERVICES:
[User Service] [Product Service] [Order Service] [Payment Service]
Each has OWN codebase, OWN database, OWN deployment
```

| Feature     | Monolith           | Microservices          |
|------------|-------------------|------------------------|
| Codebase    | Single             | Multiple               |
| Deployment  | All at once        | Independent            |
| Scaling     | Scale everything   | Scale only what's needed|
| Failure     | All down           | Isolated               |
| Database    | Shared             | One per service        |
| Complexity  | Simple initially   | Complex from start     |

---

## Why Microservices?
- Scale independently — high traffic on payments? Scale only payment service
- Deploy independently — update one service without deploying everything
- Fault isolation — one service fails, others continue
- Technology flexibility — each team can use different languages/DB
- Smaller codebases — easier to maintain

**Disadvantages:**
- Complex infrastructure
- Network latency between services
- Distributed data consistency problems
- Harder debugging

---

## Service Communication

### Synchronous (waits for response)
- **REST API:** HTTP-based, most common
- **gRPC:** Faster, uses Protocol Buffers, ideal for internal services

### Asynchronous (fire and forget)
- **Kafka / RabbitMQ:** Service publishes event, others consume
```
Order Service → Kafka → Payment Service
                      → Email Service
                      → Analytics Service
```

**When sync:** Need immediate response (check stock, get user info)
**When async:** Don't need immediate response (send email, process payment)

---

## API Gateway
Single entry point for all client requests.
```
Client App
    |
[API Gateway]  ← single entry
    |      |      |
[User]  [Orders]  [Products]
```
API Gateway does: routing, authentication, rate limiting, load balancing, logging.

---

## Service Discovery
Services have dynamic IPs. Service Registry tracks where each service is.
```
Service A → asks Registry: "Where is Service B?"
Registry → returns: "10.0.0.5:8080"
Service A → calls that address
```
Tools: Consul, Eureka, Kubernetes DNS.

---

## Fault Tolerance Patterns

### Circuit Breaker
Stop calling a failing service. Like an electrical breaker.
```
5 failures → Circuit OPEN → Skip calls for 30s → Try again → OK → Circuit CLOSED
```
Tools: Resilience4j, Netflix Hystrix.

### Retry with Exponential Backoff
```
Try 1 → fail → wait 1s
Try 2 → fail → wait 2s
Try 3 → fail → wait 4s → give up
```

### Timeout
Don't wait forever. Set maximum wait time.

---

## Distributed Tracing
Assign ONE trace ID to a request, pass through all services.
```
Request → Trace ID: abc123
→ Service A [abc123] → Service B [abc123] → Service C [abc123]
See full journey with timing!
```
Tools: Jaeger, Zipkin, AWS X-Ray.

---

## Microservices Interview Questions & Answers

**Q: What is a microservice?**
A: Small, independently deployable service that does ONE thing. Own codebase, database, and deployment pipeline.

**Q: When NOT to use microservices?**
A: Small teams, early startups, simple apps. Start with monolith, split when truly needed.

**Q: What is API Gateway?**
A: Single entry point. Handles routing, auth, rate limiting.

**Q: How do microservices communicate?**
A: Sync: REST or gRPC. Async: Kafka/RabbitMQ.

**Q: What is Circuit Breaker?**
A: Stop calling failing service after repeated failures. Prevents cascading failures.

**Q: How to handle distributed transactions?**
A: SAGA pattern — series of local transactions with compensating actions if one fails.

---

## Memory Trick
```
Microservices = Restaurant Kitchen
Each service = One chef (does only one thing)
API Gateway = Head waiter (routes orders)
Kafka = Order tickets between stations
Circuit Breaker = "Station overwhelmed, pause orders"
Service Discovery = Staff directory
```

---

# PART 4 — AWS ECS

## What is AWS ECS?
ECS (Elastic Container Service) = AWS's service to run Docker containers at scale in the cloud.

**Analogy:** You have many workers (containers). ECS is the manager who assigns jobs, restarts them if they fail, adds more when busy.

---

## Key ECS Concepts

### Cluster
Group of servers/resources where containers run. Like a building.

### Task Definition
Blueprint (like Dockerfile for ECS). Describes: Docker image, CPU, memory, ports, env vars.

### Task
A running instance of a Task Definition. Like `docker run` but managed by ECS.

### Service
Ensures a specified number of Tasks are ALWAYS running.
```
ECS Service → "I need 3 tasks running always"
Task 1 crashes → Service immediately starts Task 4
```

---

## Launch Types

### Fargate (Serverless)
AWS manages servers for you. Pay per task.
- No server management
- Pay per task
- Slightly more expensive

### EC2 Launch Type
You manage the EC2 servers.
- More control
- Cheaper at scale
- You manage servers (patching, scaling)

**Rule:** Start with Fargate. Switch to EC2 when scale justifies it.

---

## ECR (Elastic Container Registry)
AWS's private Docker registry.
```bash
aws ecr get-login-password | docker login --username AWS --password-stdin <ECR_URL>
docker tag myapp:latest <ECR_URL>/myapp:latest
docker push <ECR_URL>/myapp:latest
```

---

## ECS Deployment Flow
```
1. Developer writes code
2. Docker image built
3. Image pushed to ECR
4. Update Task Definition (new image URI)
5. Update ECS Service
6. ECS rolling deployment:
   → Starts new tasks
   → Health checks pass
   → Stops old tasks
7. Load Balancer routes to new tasks
```

---

## ECS Architecture
```
Internet
    |
[Application Load Balancer]
    |
[ECS Service]
    |
[Task 1] [Task 2] [Task 3]
    |
[ECS Cluster — Fargate or EC2]
```

---

## Auto Scaling
```
CPU > 70% → Add 2 tasks
CPU < 30% → Remove 1 task
```
Types: Target Tracking, Step Scaling.

---

## IAM Roles in ECS
- **Task Execution Role:** ECS agent permissions (pull images, write logs)
- **Task Role:** YOUR app's permissions (read S3, write DynamoDB)

---

## ECS Interview Questions & Answers

**Q: Task vs Service?**
A: Task = running container instance. Service = manages tasks, keeps N running, replaces failed ones.

**Q: Fargate vs EC2?**
A: Fargate = serverless, AWS manages servers. EC2 = you manage, more control, better at scale/cost.

**Q: How does ECS deployment work?**
A: New image → ECR → Update task definition → Update service → Rolling update → Health check → Old tasks removed.

**Q: What is a Task Definition?**
A: JSON blueprint: image, CPU, memory, ports, env vars, logging config.

**Q: How do containers access AWS services?**
A: Via IAM Task Role. No credentials in code — uses IAM role.

---

# PART 5 — TERRAFORM

## What is Terraform?
Terraform lets you describe your entire infrastructure as CODE, then automatically creates it.

**Analogy:** Instead of manually clicking in AWS console, you write a blueprint (code) and Terraform builds everything for you. Build the same infra in 5 environments? Run same code 5 times!

---

## Infrastructure as Code (IaC)
Before: Click around in AWS console manually. Error-prone. Not repeatable.
After: Write code → run it → infrastructure created automatically.

**Benefits:** Version control infra, reproduce environments identically, review infra changes like code.

---

## Core Terraform Concepts

### Providers
```hcl
provider "aws" { region = "us-east-1" }
```

### Resources
```hcl
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t3.micro"
}
```

### Variables
```hcl
variable "environment" { default = "dev" }
resource "aws_s3_bucket" "data" {
  bucket = "myapp-${var.environment}-data"
}
```

### Outputs
```hcl
output "server_ip" {
  value = aws_instance.web.public_ip
}
```

### State File
Terraform tracks what it created in terraform.tfstate.
Compares desired state (code) vs current state (state file) to know what to change.
**NEVER manually edit. Store remotely (S3 + DynamoDB).**

---

## Core Commands
```bash
terraform init      # download providers/plugins
terraform plan      # preview: what will change?
terraform apply     # create/change infrastructure
terraform destroy   # delete everything
terraform fmt       # format code
terraform validate  # check for errors
```

---

## Modules — Reusable Terraform code
```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0.0"
  name    = "my-vpc"
  cidr    = "10.0.0.0/16"
}
```

---

## Remote State
```hcl
terraform {
  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "prod/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-lock"
  }
}
```

---

## Terraform Interview Questions & Answers

**Q: What is Terraform State?**
A: File tracking what infrastructure Terraform created. Compares code vs state to determine changes needed.

**Q: What if state file is deleted?**
A: Terraform thinks nothing exists. Will try to CREATE everything again. Use remote state to prevent loss.

**Q: What is terraform plan?**
A: Preview of what WILL happen. Shows creates (+), changes (~), destroys (-). Always run before apply!

**Q: Terraform vs CloudFormation?**
A: Terraform: multi-cloud, open source, HCL. CloudFormation: AWS only, managed by AWS, YAML/JSON.

**Q: How to manage secrets?**
A: Never hardcode. Use AWS Secrets Manager, SSM Parameter Store, HashiCorp Vault, or env vars.

**Q: What is a module?**
A: Reusable Terraform code. Like a function — write once, use many times.

---

## Terraform Best Practices
- Always use remote state (S3 + DynamoDB lock)
- Use modules for reusable infrastructure
- Never commit .tfstate to Git
- Never hardcode secrets
- Always run plan in CI/CD before applying
- Tag all resources (owner, environment, project)

## Memory Trick
```
Terraform = Builder with blueprints
.tf files = blueprints (what you want)
State file = inventory (what exists)
Plan = "Here's what I'll build" (preview)
Apply = Actually builds it
Destroy = Demolishes everything
Provider = Contractor for AWS/GCP/Azure
Module = Pre-made blueprint (reuse it!)
```

---

# PART 6 — KUBERNETES

## What is Kubernetes?
Kubernetes (K8s) is a smart manager for your Docker containers.
Makes sure right number of containers are running, restarts failed ones, scales automatically.

**Analogy:** You have 100 workers (containers). K8s is the HR manager + scheduler who keeps everything working, replaces sick workers, hires more when busy.

---

## Why Kubernetes?
Problem: 100 containers across 50 servers. How do you keep them running? Scale them? Deploy without downtime? Route traffic?
**Kubernetes solves all of this.**

---

## Kubernetes Architecture

```
CONTROL PLANE (Master)
┌─────────────────────────────────────┐
│ API Server | Scheduler | Controller │
│ etcd (database of cluster state)    │
└─────────────────────────────────────┘
         |
WORKER NODES
┌──────────┐  ┌──────────┐  ┌──────────┐
│  Node 1  │  │  Node 2  │  │  Node 3  │
│ kubelet  │  │ kubelet  │  │ kubelet  │
│[Pod][Pod]│  │[Pod][Pod]│  │[Pod][Pod]│
└──────────┘  └──────────┘  └──────────┘
```

**Control Plane:**
- API Server: All communication goes through here (receptionist)
- Scheduler: Decides which node to run new pods on
- Controller Manager: Watches and ensures desired state
- etcd: Database storing cluster state — CRITICAL, backup regularly!

**Worker Node:**
- kubelet: Agent on each node, follows control plane instructions
- kube-proxy: Handles networking/routing
- Container Runtime: Actually runs containers (Docker/containerd)

---

## Core Kubernetes Objects

### Pod — Smallest unit, usually ONE container
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: app
      image: nginx
      ports:
        - containerPort: 80
```

### Deployment — Manages a set of identical pods
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.21
```

### Service — Stable way to access pods (pods have changing IPs)
Types:
- **ClusterIP:** Internal only (default)
- **NodePort:** Exposed on each node's port
- **LoadBalancer:** Creates cloud load balancer

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
  type: LoadBalancer
```

### Ingress — HTTP/HTTPS routing based on URL path
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: myapp.com
      http:
        paths:
          - path: /api
            pathType: Prefix
            backend:
              service: { name: api-service, port: { number: 80 } }
```

### ConfigMap — Store non-sensitive config
```yaml
apiVersion: v1
kind: ConfigMap
data:
  DATABASE_HOST: "postgres-service"
  APP_ENV: "production"
```

### Secret — Sensitive data (base64 encoded)
```yaml
apiVersion: v1
kind: Secret
type: Opaque
data:
  password: cGFzc3dvcmQ=  # base64
```

### Namespace — Logical separation
```bash
kubectl create namespace dev
kubectl get pods -n dev
```

---

## Special Workload Types

| Type        | Use for                                      |
|------------|----------------------------------------------|
| StatefulSet | Databases (stable names, stable storage)     |
| DaemonSet   | One pod per EVERY node (log agents, monitors)|
| Job         | Run until completion (batch, migrations)     |
| CronJob     | Scheduled jobs (like Linux cron)             |

---

## HPA (Horizontal Pod Autoscaler)
Automatically scale pods based on CPU/memory.
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
spec:
  scaleTargetRef:
    kind: Deployment
    name: nginx-deployment
  minReplicas: 2
  maxReplicas: 10
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
```

---

## Rolling Updates (Zero Downtime)
```
[v1][v1][v1][v1] → [v1][v1][v1][v2] → [v1][v2][v2][v2] → [v2][v2][v2][v2]
```
Always some pods running → zero downtime!

```bash
kubectl rollout undo deployment/nginx  # rollback
```

---

## Persistent Storage
- **PersistentVolume (PV):** Actual storage in cluster
- **PersistentVolumeClaim (PVC):** Request for storage by a pod ("I need 10GB")

---

## kubectl Commands
```bash
kubectl get pods                    # list pods
kubectl describe pod my-pod         # detailed info
kubectl logs my-pod                 # container logs
kubectl exec -it my-pod -- bash     # shell into pod
kubectl apply -f deployment.yaml    # apply config
kubectl rollout undo deployment/app # rollback
kubectl top pods                    # CPU/memory usage
kubectl get events                  # cluster events
```

---

## Helm — Package manager for Kubernetes
```bash
helm install my-release nginx/nginx-ingress
helm upgrade my-release nginx/nginx-ingress
helm rollback my-release 1
```

---

## Kubernetes Interview Questions & Answers

**Q: What is a Pod?**
A: Smallest deployable unit. Usually one container. Has its own IP, storage, network namespace.

**Q: Deployment vs StatefulSet?**
A: Deployment: stateless apps, pods are interchangeable. StatefulSet: stateful apps (DBs), pods have stable identity and storage.

**Q: What happens when a node fails?**
A: Controller Manager detects failure. Pods rescheduled to other healthy nodes. This is self-healing!

**Q: Service types?**
A: ClusterIP = internal. NodePort = exposed on node. LoadBalancer = cloud LB. Ingress = HTTP routing.

**Q: What is HPA?**
A: Horizontal Pod Autoscaler. Automatically scales pod count based on CPU, memory, or custom metrics.

**Q: Zero-downtime deployment?**
A: Rolling update strategy. K8s gradually replaces old pods with new ones.

**Q: What is etcd?**
A: Key-value store — K8s brain/database. Stores entire cluster state. Critical — backup regularly!

**Q: How does Service Discovery work?**
A: Built-in DNS. Every Service gets DNS name: `my-service.my-namespace.svc.cluster.local`

---

## Memory Trick
```
Kubernetes = Airport Manager
Pod = Airplane (holds passengers/containers)
Node = Airport terminal (runs airplanes)
Deployment = Airline schedule (how many planes)
Service = Boarding gate (stable access to pods)
Ingress = Airport entrance (routes to correct gate)
HPA = Add more flights when demand is high
Namespace = Different terminals (dev/prod)
```

---

# PART 7 — KAFKA

## What is Kafka?
Kafka is a super-fast distributed message bus. Services communicate by PUBLISHING and CONSUMING events.

**Analogy:** News broadcast — Journalists (Producers) write stories → TV Network (Kafka) → Viewers (Consumers) watch. Multiple viewers watch the SAME story. Story stored for days. New viewers can watch old stories (replay).

---

## Why Kafka?

| Problem                              | Kafka Solution                       |
|-------------------------------------|--------------------------------------|
| Notify 10 services of one event     | Publish once, all 10 consume         |
| Millions of events/second           | Kafka handles millions/sec           |
| Message lost if consumer is down    | Kafka stores messages for days       |
| Need to replay past events          | Kafka replays from any offset        |

---

## Core Kafka Concepts

### Producer — Sends messages to Kafka
### Consumer — Reads messages from Kafka
### Broker — A Kafka server (cluster = multiple brokers)

### Topic — Named stream/channel of messages
```
Topics: user-events, order-events, payment-events
```

### Partition — Topics split for parallelism
```
Topic: orders
  Partition 0: [msg1, msg4, msg7]
  Partition 1: [msg2, msg5, msg8]
  Partition 2: [msg3, msg6, msg9]
```
Messages with same key → always same partition (ensures ORDER).

### Offset — Position of message in partition
Consumers track offset to know where they are. Like a page number.

### Consumer Group — Multiple consumers sharing work
```
Topic: orders (3 partitions)
Consumer Group: payment-service

Consumer A → Partition 0
Consumer B → Partition 1
Consumer C → Partition 2
```
Each partition consumed by ONLY ONE consumer in the group.

---

## Kafka Architecture
```
Producers
   |
[Kafka Cluster]
  [Broker 1]  [Broker 2]  [Broker 3]
  Partitions replicated across brokers
   |
Consumers (Consumer Groups)
```

---

## Replication — Fault Tolerance
```
Partition 0 Leader: Broker 1
Partition 0 Replicas: Broker 2, Broker 3

If Broker 1 fails → Broker 2 becomes leader automatically
```
Replication Factor 3 = one leader + two replicas. Standard for production.

---

## Message Flow (End to End)
```
1. Producer sends message to Topic "orders", key="user123"
2. Kafka determines partition (hash of key)
3. Message stored with next offset
4. Replicated to replica brokers
5. Consumer Group polls for new messages
6. Consumer reads, processes, commits offset
7. If consumer crashes before commit → re-reads same message
   (at-least-once delivery)
```

---

## Kafka vs RabbitMQ

| Feature        | Kafka                   | RabbitMQ              |
|---------------|-------------------------|-----------------------|
| Type           | Event streaming          | Message queue         |
| Throughput     | Millions/sec            | Thousands/sec         |
| Storage        | Days/weeks              | Until consumed        |
| Replay         | Yes                     | No                    |
| Use case       | Event streaming, logs   | Task queues, RPC      |
| Complexity     | Higher                  | Lower                 |

---

## Kafka Interview Questions & Answers

**Q: What is Kafka and why use it?**
A: Distributed event streaming. High-throughput, real-time data pipelines. Publish once, multiple services consume.

**Q: What is a Consumer Group?**
A: Group of consumers sharing topic consumption. Each partition consumed by exactly one consumer. Enables parallel processing.

**Q: What is an offset?**
A: Position of message in partition. Consumers track offset to know what they've processed.

**Q: What happens if consumer crashes?**
A: If offset not committed, consumer re-reads same messages (at-least-once). For exactly-once: use idempotent consumers.

**Q: How does Kafka achieve fault tolerance?**
A: Replication. Each partition copied to multiple brokers. Leader fails → replica becomes new leader.

**Q: How to ensure message ordering?**
A: Use message keys. Same key → same partition → ordered within partition.

**Q: What is retention?**
A: How long Kafka stores messages. Default 7 days. Consumers can replay old events within window.

---

## Memory Trick
```
Kafka = News Broadcasting System
Producer = Journalist (writes news)
Topic = TV Channel (sports, news, weather)
Partition = Multiple towers broadcasting same channel
Broker = TV Transmission tower
Consumer = Viewer watching TV
Consumer Group = Household sharing one TV
Offset = Which episode you last watched
Retention = How long show stays available
```

---

# PART 8 — CI/CD & DEPLOYMENT

## What is CI/CD?

**CI = Continuous Integration**
Every commit triggers automatic testing and building.

**CD = Continuous Delivery**
Automatically prepare code for release. Deploy to staging auto. Prod may need manual approval.

**CD = Continuous Deployment**
Automatically deploy to PRODUCTION after all checks pass. No human needed.

```
Write Code → Commit → AUTO: Test → AUTO: Build → AUTO: Deploy
```

---

## Why CI/CD?
Without: Manual testing takes days. Deploys are risky. Bugs found late.
With: Bugs caught immediately. Deploys automated. Releases are small and frequent.

---

## Typical CI/CD Pipeline
```
Developer pushes code
         |
    [BUILD]  ← compile, create Docker image
         |
    [TEST]   ← unit tests, integration tests, security scan
         |
    [PUSH]   ← push Docker image to ECR
         |
    [DEPLOY] ← deploy to staging, then production
```

---

## GitHub Actions Example
```yaml
name: CI/CD
on:
  push:
    branches: [main]
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build
        run: docker build -t myapp:${{ github.sha }} .
      - name: Test
        run: docker run myapp:${{ github.sha }} npm test
      - name: Deploy
        run: ./deploy.sh
```

---

## Deployment Strategies

### Rolling Deployment (default, no extra servers)
```
[v1][v1][v1][v1] → gradually replace → [v2][v2][v2][v2]
```
Zero downtime. Brief mix of old/new. Slow rollback.

### Blue-Green Deployment (instant rollback, 2x servers)
```
Blue (v1) = LIVE   Green (v2) = STANDBY
Switch: Green becomes LIVE, Blue becomes STANDBY
Rollback: Switch back to Blue — instant!
```

### Canary Deployment (low risk, real traffic testing)
```
95% → OLD version
 5% → NEW version (canary)
All OK? → 50/50 → All OK? → 100% new
```

---

## Comparison: Rolling vs Blue-Green vs Canary

| Feature     | Rolling          | Blue-Green      | Canary           |
|------------|-----------------|-----------------|------------------|
| Extra servers | No            | Yes (2x temp)   | No               |
| Rollback   | Slow            | Instant         | Easy             |
| Risk       | Low             | Very Low        | Very Low         |
| Traffic mix | Brief           | All-at-once     | Gradual          |

---

## Real Production Deployment Flow
```
1. Developer merges PR to main
2. GitHub Actions triggered
3. Unit tests (5 min)
4. Integration tests (10 min)
5. Security scan (Snyk/SonarQube)
6. Build Docker image, tag with git SHA
7. Push to ECR
8. Deploy to STAGING
9. Run smoke tests on staging
10. Manual approval (optional)
11. Deploy to PRODUCTION (canary/rolling)
12. Monitor: error rate, latency, CPU
13. Auto-rollback if error rate spikes
```

---

## Rollback
```bash
# Kubernetes
kubectl rollout undo deployment/myapp

# ECS
# Update task definition to previous image tag

# Blue-Green
# Switch load balancer back to Blue
```

---

## CI/CD Interview Questions & Answers

**Q: CI vs CD?**
A: CI = automatically test and build on every commit. CD = automatically deploy to staging or production.

**Q: Blue-Green deployment?**
A: Two identical environments. Switch all traffic at once. Instant rollback by switching back. Costs 2x temporarily.

**Q: Canary deployment?**
A: Send small % of traffic to new version. Gradually increase if no issues. Low risk, real traffic testing.

**Q: How to achieve zero-downtime deployment?**
A: Rolling updates, blue-green, or canary. Health checks ensure new version works before removing old.

**Q: What to monitor after deployment?**
A: Error rates, latency, CPU/memory, business KPIs. Watch 15-30 minutes post-deployment.

---

# PART 9 — DEVOPS & CLOUD BASICS

## What is DevOps?
Dev + Ops working TOGETHER. Same team writes code AND deploys/operates it.

Goals: Faster releases, higher reliability, automation everywhere.

---

## Linux Basics
```bash
ls -la              # list files
cat file.txt        # show file contents
grep "error" log.txt # search in file
tail -f app.log     # watch log live
ps aux              # list all processes
kill PID            # kill process
chmod 755 script.sh # set permissions
curl http://localhost:8080  # HTTP request
netstat -tulpn      # show open ports
df -h               # disk space
free -h             # memory usage
top / htop          # system resources
```

---

## Networking Basics

### HTTP Status Codes
```
2xx = Success (200 OK, 201 Created)
3xx = Redirect (301 Moved, 302 Found)
4xx = Client error (400 Bad Request, 401 Unauthorized, 404 Not Found)
5xx = Server error (500 Internal Error, 503 Unavailable)
```

### DNS — Translates domain names to IPs
```
google.com → 142.250.80.46   (like phone book for internet)
```

### Load Balancer — Distributes traffic across servers
```
Users → Load Balancer → Server 1 / Server 2 / Server 3
```

### Reverse Proxy — Sits in front of servers, forwards requests
Benefits: SSL termination, caching, hiding backend.
Tool: Nginx.

### CDN — Servers globally caching static content
User in India gets content from India CDN node → faster!

---

## Monitoring & Observability

**Three Pillars:**
- **Metrics:** Numbers over time (CPU%, requests/sec, error rate)
- **Logs:** Text records of events
- **Traces:** Track a request through all services

### Prometheus
Scrapes metrics from apps every N seconds. Stores time-series data.

### Grafana
Dashboard tool. Reads Prometheus data → beautiful graphs.

```
App → exposes /metrics → Prometheus scrapes → Grafana shows dashboard
```

### ELK Stack (Elasticsearch + Logstash + Kibana)
- Logstash: Collect and transform logs
- Elasticsearch: Store and search logs (billions of records)
- Kibana: Visualize logs and dashboards

```
App logs → Logstash → Elasticsearch → Kibana
```

---

## AWS Key Services
```
Compute:    EC2 (VMs), ECS (containers), Lambda (serverless)
Storage:    S3 (object), EBS (block), EFS (file)
Database:   RDS (SQL), DynamoDB (NoSQL), ElastiCache (Redis)
Network:    VPC, Route53 (DNS), CloudFront (CDN), ELB (load balancer)
Security:   IAM, KMS, Secrets Manager, WAF
Monitoring: CloudWatch (metrics+logs), X-Ray (tracing)
```

### IAM — Control WHO can do WHAT
**Principle of Least Privilege:** Give ONLY the permissions needed. Nothing more.

---

# PART 10 — INTERVIEW QUESTIONS BANK

## Beginner Questions
1. What is Git? Why is version control important?
2. What is Docker? How is it different from a VM?
3. What is a Dockerfile?
4. What is CI/CD?
5. What is a microservice?
6. What is Kubernetes and why is it needed?
7. What is Kafka used for?
8. What is Terraform?
9. What is AWS ECS?
10. What are the main HTTP status codes?

## Intermediate Questions
1. Explain GitFlow branching strategy.
2. What is Docker multi-stage build and why use it?
3. What is an API Gateway in microservices?
4. Explain Blue-Green vs Canary deployment.
5. Kubernetes Deployment vs StatefulSet?
6. What is a Kafka Consumer Group?
7. What is Terraform state file?
8. How does ECS auto-scaling work?
9. What is Circuit Breaker pattern?
10. How do you achieve zero-downtime deployment?

## Advanced Questions
1. How do you debug a pod in CrashLoopBackOff?
2. Explain Kafka replication and leader election.
3. How to handle Terraform state conflicts in a team?
4. What is SAGA pattern in microservices?
5. How does Kubernetes HPA work internally?
6. What is distributed tracing and why is it needed?
7. What is etcd and why is it critical?
8. How would you design a CI/CD pipeline for microservices?
9. What is the difference between rolling update and recreate strategy?
10. How do you secure secrets in Kubernetes?

## Senior / Architect Level Questions
1. Design deployment architecture for high-traffic e-commerce.
2. How would you migrate a monolith to microservices?
3. Design zero-downtime deployment for a critical payment service.
4. How to handle database migrations in microservices deployment?
5. What is your observability strategy for distributed systems?
6. How would you design a multi-region AWS deployment?
7. Explain CAP theorem and how it affects microservice design.
8. How do you handle service-to-service authentication?
9. Strategy for Kubernetes cluster upgrades?
10. How to prevent cascading failures in microservices?

## Scenario-Based Questions

**"Production is down. 5xx errors spiking. What do you do?"**
→ Check load balancer → Check service logs → Check recent deployments
→ Check CPU/memory → Rollback if recent deploy → Escalate if unknown

**"A pod is stuck in Pending state. Why and how to fix?"**
→ kubectl describe pod → check events
→ Causes: insufficient resources, no matching node, image pull error
→ Fix: add resources, fix image name, check node taints

**"Kafka consumer lag is increasing. Why?"**
→ Consumers can't keep up with producers
→ Fix: add more consumers (up to partition count), optimize processing

**"Terraform apply fails halfway. What now?"**
→ Some resources created, some not
→ Check state, manually import created resources or destroy and retry

**"Docker image is 2GB. How to reduce?"**
→ Alpine base image, multi-stage builds, .dockerignore,
→ Remove dev dependencies, clean apt/package caches

## Debugging Questions
- CrashLoopBackOff → `kubectl logs pod-name --previous`
- ImagePullBackOff → Wrong image name, tag, or registry credentials
- Pod Pending → Insufficient resources or unschedulable node
- 503 from service → No healthy pods matching service selector
- High Kafka consumer lag → Consumer too slow, add more consumers
- Terraform state lock → Stale lock, force-unlock carefully

---

# PART 11 — IMPORTANT COMPARISONS

## Docker vs VM

| Feature    | VM                  | Docker            |
|-----------|---------------------|-------------------|
| Size       | GBs (full OS)       | MBs (shares OS)   |
| Startup    | Minutes             | Seconds           |
| Isolation  | Strong (own OS)     | Process-level     |
| Performance| Slower              | Near-native       |
| Use case   | Full OS needed      | App packaging     |

## Monolith vs Microservices

| Feature     | Monolith           | Microservices         |
|------------|-------------------|-----------------------|
| Codebase    | Single            | Multiple              |
| Deployment  | All at once       | Independent           |
| Scaling     | Scale everything  | Scale per service     |
| Failure     | All down          | Isolated              |
| Database    | Shared            | One per service       |
| Complexity  | Low initially     | High from start       |

## ECS vs Kubernetes

| Feature      | ECS              | Kubernetes (EKS)     |
|-------------|-----------------|----------------------|
| Complexity   | Low             | High                 |
| AWS-native   | Yes (deep)      | Via EKS              |
| Multi-cloud  | No              | Yes                  |
| Learning     | Low             | High                 |
| Best for     | AWS-focused     | Complex, large scale |

## Kafka vs RabbitMQ

| Feature     | Kafka            | RabbitMQ           |
|------------|-----------------|---------------------|
| Throughput  | Millions/sec     | Thousands/sec       |
| Storage     | Days/weeks       | Until consumed      |
| Replay      | Yes              | No                  |
| Complexity  | Higher           | Lower               |
| Use case    | Event streaming  | Task queues         |

## Docker Swarm vs Kubernetes

| Feature     | Docker Swarm   | Kubernetes       |
|------------|---------------|-----------------|
| Complexity  | Simple         | Complex          |
| Auto-scaling| No            | Yes (HPA)        |
| Community   | Declining      | Huge, growing    |
| Production  | Small setups   | Large enterprise |

## Terraform vs CloudFormation

| Feature     | Terraform      | CloudFormation   |
|------------|---------------|-----------------|
| Cloud       | Multi-cloud   | AWS only         |
| Language    | HCL           | YAML/JSON        |
| State       | External file | Managed by AWS   |
| Community   | Very large    | AWS-specific     |

## CI vs CD

| Feature    | CI                       | CD                          |
|-----------|-------------------------|------------------------------|
| Stands for | Continuous Integration  | Continuous Delivery/Deploy   |
| When runs  | Every commit            | After CI passes              |
| Does       | Build + Test            | Deploy to staging/prod       |

## Rolling vs Blue-Green vs Canary

| Feature        | Rolling     | Blue-Green   | Canary        |
|---------------|------------|--------------|---------------|
| Extra servers  | No         | Yes (2x)     | No            |
| Rollback speed | Slow       | Instant      | Easy          |
| Traffic mix    | Brief      | All-at-once  | Gradual       |
| Cost           | Lower      | Higher       | Lower         |

## Pod vs Container

| Feature     | Container        | Pod (Kubernetes)     |
|------------|-----------------|----------------------|
| Runtime     | Docker           | K8s concept          |
| What it is  | Running process  | Wrapper around container|
| Networking  | Own              | Shared within pod    |
| Scaling     | Docker scales    | K8s scales pods      |

## Service vs Ingress (Kubernetes)

| Feature    | Service         | Ingress               |
|-----------|----------------|-----------------------|
| Layer      | L4 (TCP/UDP)   | L7 (HTTP/HTTPS)       |
| Routing    | By port        | By URL path/hostname  |
| SSL        | No             | Yes                   |
| Use case   | Internal access| External HTTP access  |

---

# PART 12 — PRODUCTION SCENARIOS & ARCHITECTURE

## Scenario 1: High Traffic E-Commerce Architecture
```
Internet → CloudFront (CDN)
        → Route53 (DNS)
        → Application Load Balancer
        → ECS/Kubernetes cluster
            → Product Service (3 replicas)
            → Order Service (5 replicas)
            → Payment Service (3 replicas, multi-AZ)
            → Notification Service (2 replicas)
        → Kafka cluster (order events)
        → RDS PostgreSQL (Multi-AZ)
        → ElastiCache Redis (sessions + cache)
        → S3 (images, static assets)

CI/CD: GitHub → GitHub Actions → ECR → ECS Rolling Deploy
Monitoring: CloudWatch + Grafana dashboards
Alerts: PagerDuty for on-call
```

## Scenario 2: Zero-Downtime Production Deployment
```
1. Feature branch → PR → Code Review → Merge to main
2. CI: Tests + security scan pass
3. Docker image built, tagged with git SHA
4. Pushed to ECR
5. Deploy to STAGING (identical to prod)
6. Smoke tests pass
7. Canary: 5% traffic → new version
8. Monitor 15 min: error rates, latency OK
9. Gradually: 20% → 50% → 100%
10. Old tasks drained and removed
```

## Scenario 3: Kafka-Driven Order Processing
```
1. User places order → Order Service
2. Order Service publishes "OrderPlaced" to Kafka
3. Kafka: Topic "orders", 10 partitions
4. Consumers react independently:
   - Payment Service: charges customer
   - Inventory Service: reserves items
   - Email Service: sends confirmation
   - Analytics: records for dashboards
5. Payment publishes "PaymentSucceeded"
6. Fulfillment Service ships order

Fault Tolerance: If Email Service is down, orders still process.
Email catches up when it comes back (Kafka retains messages).
```

---

# QUICK REVISION CHEAT SHEET

## GIT
- init/clone → add/commit → push/pull → branch/merge
- GitFlow: main → develop → feature/release/hotfix
- Merge = history preserved | Rebase = linear history
- PR → Code Review → Merge → CI/CD triggers

## DOCKER
- Dockerfile → Image → Container
- docker build / docker run / docker push
- Volume = persistent storage
- Compose = multi-container
- Multi-stage = smaller images
- Registry = ECR/Docker Hub

## MICROSERVICES
- One service = one responsibility + own DB
- API Gateway = single entry point
- Sync: REST/gRPC | Async: Kafka
- Circuit Breaker → stop calling failing service
- Distributed Tracing → trace ID across services

## ECS
- Task Definition → Task → Service → Cluster
- Fargate = serverless | EC2 = you manage
- ECR = private Docker registry
- Rolling deployment with health checks

## TERRAFORM
- init → plan → apply → destroy
- State file = tracks what exists (store in S3!)
- Modules = reusable code
- Never hardcode secrets

## KUBERNETES
- Pod → Deployment → Service → Ingress
- ConfigMap (config) | Secret (sensitive)
- HPA = auto-scale pods on CPU/memory
- Rolling update = zero downtime
- StatefulSet = databases | DaemonSet = every node
- etcd = cluster brain (backup it!)

## KAFKA
- Producer → Topic (Partitions) → Consumer Group
- Offset = where consumer is
- Replication = fault tolerance
- Retention = messages stored for days
- Consumer Group = parallel consumption

## CI/CD
- CI: build + test every commit
- CD: auto deploy
- Rolling → gradual, no extra servers
- Blue-Green → instant rollback, 2x cost
- Canary → gradual % rollout, lowest risk

## DEVOPS/CLOUD
- Prometheus: scrape metrics → Grafana: visualize
- ELK: collect/search/visualize logs
- IAM: who can do what (least privilege!)
- VPC: your private network in AWS

---

# INTERVIEW DAY TIPS

## Key Phrases That Impress Interviewers
- "We used Canary deployment to minimize production risk"
- "Circuit breaker pattern prevented cascading failures"
- "Stored Terraform state in S3 with DynamoDB locking for team safety"
- "Zero-downtime deployment with rolling updates in Kubernetes"
- "Distributed tracing with Jaeger to debug cross-service latency"
- "Consumer groups allowed us to independently scale each service"
- "Followed principle of least privilege for all IAM roles"
- "Multi-stage Docker builds reduced our image size by 80%"

## "Tell Me About a Production Incident" Formula
1. What happened (briefly)
2. How you detected it (monitoring/alert)
3. How you diagnosed it (tools, logs, metrics)
4. How you fixed it (rollback, hotfix)
5. What you did to prevent it happening again (post-mortem)

## Common Opening Questions
- "Walk me through a deployment you did"
- "How do you handle a production outage?"
- "What is your approach to microservices communication?"
- "Explain your CI/CD pipeline"

---

# ============================================================
# END OF GUIDE
# Study order: Git → Docker → Microservices → Kubernetes
#              → Kafka → CI/CD → ECS → Terraform → Cloud
# Focus: CONCEPTS > COMMANDS
# GOOD LUCK IN YOUR INTERVIEWS!
# ============================================================
