# DevOps Command Hub 🚀

A comprehensive collection of essential DevOps commands and best practices for various tools and platforms. This hub serves as a quick reference guide for DevOps engineers, SREs, and developers.

## 📚 Table of Contents

- [Docker](#docker)
- [Kubernetes](#kubernetes)
- [Git](#git)
- [AWS CLI](#aws-cli)
- [Terraform](#terraform)
- [Ansible](#ansible)
- [Jenkins](#jenkins)
- [CI/CD](#cicd)
- [Linux/Unix](#linuxunix)
- [Networking](#networking)

---

## Docker

### Basic Commands
```bash
# Build an image
docker build -t image_name:tag .

# Run a container
docker run -d -p 8080:80 --name container_name image_name

# List running containers
docker ps

# List all containers
docker ps -a

# Stop a container
docker stop container_name

# Remove a container
docker rm container_name

# List images
docker images

# Remove an image
docker rmi image_name

# View logs
docker logs container_name

# Execute command in running container
docker exec -it container_name /bin/bash

# View container resource usage
docker stats

# Inspect container details
docker inspect container_name
```

### Docker Compose
```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f

# Rebuild services
docker-compose up -d --build

# List services
docker-compose ps
```

### Cleanup
```bash
# Remove unused containers, networks, images
docker system prune -a

# Remove all stopped containers
docker container prune

# Remove unused volumes
docker volume prune

# Remove unused networks
docker network prune
```

---

## Kubernetes

### Cluster Management
```bash
# Get cluster info
kubectl cluster-info

# Get nodes
kubectl get nodes

# Describe a node
kubectl describe node node_name

# Get all resources
kubectl get all --all-namespaces
```

### Pod Management
```bash
# List pods
kubectl get pods

# List pods with more details
kubectl get pods -o wide

# Describe a pod
kubectl describe pod pod_name

# Get pod logs
kubectl logs pod_name

# Follow logs
kubectl logs -f pod_name

# Execute command in pod
kubectl exec -it pod_name -- /bin/bash

# Delete a pod
kubectl delete pod pod_name
```

### Deployment Management
```bash
# Create deployment
kubectl create deployment deployment_name --image=image_name

# Get deployments
kubectl get deployments

# Scale deployment
kubectl scale deployment deployment_name --replicas=3

# Update image
kubectl set image deployment/deployment_name container_name=new_image:tag

# Rollout status
kubectl rollout status deployment/deployment_name

# Rollback deployment
kubectl rollout undo deployment/deployment_name

# Delete deployment
kubectl delete deployment deployment_name
```

### Service Management
```bash
# Get services
kubectl get svc

# Expose deployment
kubectl expose deployment deployment_name --type=LoadBalancer --port=80

# Describe service
kubectl describe svc service_name

# Delete service
kubectl delete svc service_name
```

### ConfigMap & Secrets
```bash
# Create ConfigMap
kubectl create configmap config_name --from-file=config.properties

# Get ConfigMaps
kubectl get configmaps

# Create Secret
kubectl create secret generic secret_name --from-literal=password=mypass

# Get Secrets
kubectl get secrets

# Describe Secret
kubectl describe secret secret_name
```

### Namespace Management
```bash
# Get namespaces
kubectl get namespaces

# Create namespace
kubectl create namespace namespace_name

# Set default namespace
kubectl config set-context --current --namespace=namespace_name

# Delete namespace
kubectl delete namespace namespace_name
```

---

## Git

### Basic Commands
```bash
# Initialize repository
git init

# Clone repository
git clone repository_url

# Check status
git status

# Add files
git add .
git add file_name

# Commit changes
git commit -m "commit message"

# Push changes
git push origin branch_name

# Pull changes
git pull origin branch_name

# View commit history
git log
git log --oneline --graph --all
```

### Branch Management
```bash
# List branches
git branch

# Create new branch
git branch branch_name

# Switch to branch
git checkout branch_name

# Create and switch to new branch
git checkout -b branch_name

# Delete branch
git branch -d branch_name

# Delete remote branch
git push origin --delete branch_name

# Merge branch
git merge branch_name

# Rebase branch
git rebase branch_name
```

### Remote Management
```bash
# List remotes
git remote -v

# Add remote
git remote add origin url

# Remove remote
git remote remove origin

# Fetch from remote
git fetch origin

# Pull with rebase
git pull --rebase origin main
```

### Stash Commands
```bash
# Stash changes
git stash

# List stashes
git stash list

# Apply stash
git stash apply

# Pop stash
git stash pop

# Drop stash
git stash drop
```

### Undo Changes
```bash
# Discard local changes
git checkout -- file_name

# Unstage file
git reset HEAD file_name

# Amend last commit
git commit --amend

# Reset to previous commit
git reset --hard HEAD~1

# Revert commit
git revert commit_hash
```

---

## AWS CLI

### EC2
```bash
# List instances
aws ec2 describe-instances

# Start instance
aws ec2 start-instances --instance-ids instance_id

# Stop instance
aws ec2 stop-instances --instance-ids instance_id

# Terminate instance
aws ec2 terminate-instances --instance-ids instance_id

# Create key pair
aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem
```

### S3
```bash
# List buckets
aws s3 ls

# List bucket contents
aws s3 ls s3://bucket_name

# Copy file to S3
aws s3 cp file.txt s3://bucket_name/

# Copy from S3
aws s3 cp s3://bucket_name/file.txt .

# Sync directory
aws s3 sync ./local_dir s3://bucket_name/

# Create bucket
aws s3 mb s3://bucket_name

# Remove bucket
aws s3 rb s3://bucket_name --force
```

### IAM
```bash
# List users
aws iam list-users

# Create user
aws iam create-user --user-name username

# List policies
aws iam list-policies

# Attach policy to user
aws iam attach-user-policy --user-name username --policy-arn arn:aws:iam::aws:policy/PolicyName
```

### Lambda
```bash
# List functions
aws lambda list-functions

# Invoke function
aws lambda invoke --function-name function_name output.txt

# Update function code
aws lambda update-function-code --function-name function_name --zip-file fileb://function.zip
```

### CloudFormation
```bash
# List stacks
aws cloudformation list-stacks

# Create stack
aws cloudformation create-stack --stack-name stack_name --template-body file://template.yaml

# Update stack
aws cloudformation update-stack --stack-name stack_name --template-body file://template.yaml

# Delete stack
aws cloudformation delete-stack --stack-name stack_name

# Describe stack
aws cloudformation describe-stacks --stack-name stack_name
```

---

## Terraform

### Basic Commands
```bash
# Initialize Terraform
terraform init

# Format code
terraform fmt

# Validate configuration
terraform validate

# Plan changes
terraform plan

# Apply changes
terraform apply

# Apply without confirmation
terraform apply -auto-approve

# Destroy infrastructure
terraform destroy

# Show current state
terraform show

# List resources
terraform state list

# Output values
terraform output
```

### Workspace Management
```bash
# List workspaces
terraform workspace list

# Create workspace
terraform workspace new workspace_name

# Select workspace
terraform workspace select workspace_name

# Delete workspace
terraform workspace delete workspace_name
```

### State Management
```bash
# Pull remote state
terraform state pull

# Push local state
terraform state push

# Remove resource from state
terraform state rm resource_address

# Move resource in state
terraform state mv source destination

# Import existing resource
terraform import resource_address resource_id
```

---

## Ansible

### Basic Commands
```bash
# Run playbook
ansible-playbook playbook.yml

# Run with specific inventory
ansible-playbook -i inventory.ini playbook.yml

# Check syntax
ansible-playbook playbook.yml --syntax-check

# Dry run
ansible-playbook playbook.yml --check

# Run with tags
ansible-playbook playbook.yml --tags "tag_name"

# Skip tags
ansible-playbook playbook.yml --skip-tags "tag_name"

# Limit to specific hosts
ansible-playbook playbook.yml --limit "host_pattern"
```

### Ad-hoc Commands
```bash
# Ping all hosts
ansible all -m ping

# Run command on all hosts
ansible all -a "uptime"

# Copy file
ansible all -m copy -a "src=/path/to/file dest=/path/to/dest"

# Install package
ansible all -m apt -a "name=nginx state=present" --become

# Restart service
ansible all -m service -a "name=nginx state=restarted" --become
```

### Inventory
```bash
# List hosts
ansible all --list-hosts

# List groups
ansible-inventory --list

# Graph inventory
ansible-inventory --graph
```

---

## Jenkins

### Jenkins CLI
```bash
# List jobs
java -jar jenkins-cli.jar -s http://jenkins-url list-jobs

# Build job
java -jar jenkins-cli.jar -s http://jenkins-url build job_name

# Get job info
java -jar jenkins-cli.jar -s http://jenkins-url get-job job_name

# Create job
java -jar jenkins-cli.jar -s http://jenkins-url create-job job_name < config.xml

# Delete job
java -jar jenkins-cli.jar -s http://jenkins-url delete-job job_name

# Disable job
java -jar jenkins-cli.jar -s http://jenkins-url disable-job job_name

# Enable job
java -jar jenkins-cli.jar -s http://jenkins-url enable-job job_name
```

### Pipeline Snippets
```groovy
// Checkout code
checkout scm

// Build Docker image
docker.build("image_name:tag")

// Push Docker image
docker.withRegistry('https://registry.hub.docker.com', 'credentials-id') {
    docker.image("image_name:tag").push()
}

// Run in Docker container
docker.image('maven:3.8.1').inside {
    sh 'mvn clean install'
}
```

---

## CI/CD

### GitHub Actions

#### Workflow Basics
```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
```

#### Common Actions
```yaml
# Setup Node.js
- uses: actions/setup-node@v2
  with:
    node-version: '14'

# Setup Python
- uses: actions/setup-python@v2
  with:
    python-version: '3.9'

# Cache dependencies
- uses: actions/cache@v2
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}

# Docker build and push
- name: Build and push Docker image
  uses: docker/build-push-action@v2
  with:
    push: true
    tags: user/app:latest
```

### GitLab CI

#### Basic Pipeline
```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - echo "Building application"
    - npm install
    - npm run build

test:
  stage: test
  script:
    - echo "Running tests"
    - npm test

deploy:
  stage: deploy
  script:
    - echo "Deploying application"
  only:
    - main
```

---

## Linux/Unix

### System Information
```bash
# OS information
uname -a
cat /etc/os-release

# CPU information
lscpu
cat /proc/cpuinfo

# Memory information
free -h
cat /proc/meminfo

# Disk usage
df -h
du -sh /path/to/directory

# System uptime
uptime

# Running processes
ps aux
top
htop
```

### File Operations
```bash
# Find files
find /path -name "filename"
find /path -type f -mtime -7  # Modified in last 7 days

# Search in files
grep -r "pattern" /path
grep -i "pattern" file  # Case insensitive

# Count lines in file
wc -l file

# View file content
cat file
less file
head -n 10 file
tail -n 10 file
tail -f file  # Follow file

# Compare files
diff file1 file2

# Archive and compress
tar -czf archive.tar.gz directory/
tar -xzf archive.tar.gz
```

### User Management
```bash
# Add user
sudo useradd username
sudo adduser username

# Delete user
sudo userdel username

# Change password
sudo passwd username

# Add user to group
sudo usermod -aG groupname username

# List users
cat /etc/passwd

# List groups
groups username
```

### Service Management
```bash
# Systemctl (systemd)
sudo systemctl start service_name
sudo systemctl stop service_name
sudo systemctl restart service_name
sudo systemctl status service_name
sudo systemctl enable service_name
sudo systemctl disable service_name

# List all services
sudo systemctl list-units --type=service
```

### Permissions
```bash
# Change permissions
chmod 755 file
chmod +x file

# Change ownership
chown user:group file
chown -R user:group directory/

# View permissions
ls -l
```

---

## Networking

### Network Diagnostics
```bash
# Check connectivity
ping google.com

# Trace route
traceroute google.com

# DNS lookup
nslookup google.com
dig google.com

# Network interfaces
ifconfig
ip addr show

# Network statistics
netstat -tuln
ss -tuln

# Check open ports
sudo netstat -tulpn | grep LISTEN
sudo lsof -i -P -n | grep LISTEN

# Test port connection
telnet hostname port
nc -zv hostname port
```

### Firewall (UFW)
```bash
# Enable firewall
sudo ufw enable

# Disable firewall
sudo ufw disable

# Allow port
sudo ufw allow 22
sudo ufw allow 80/tcp

# Deny port
sudo ufw deny 23

# Delete rule
sudo ufw delete allow 22

# Show status
sudo ufw status
```

### Firewall (iptables)
```bash
# List rules
sudo iptables -L

# Allow port
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# Block IP
sudo iptables -A INPUT -s 192.168.1.100 -j DROP

# Save rules
sudo iptables-save > /etc/iptables/rules.v4

# Restore rules
sudo iptables-restore < /etc/iptables/rules.v4
```

### Network Utilities
```bash
# Download file
wget http://example.com/file
curl -O http://example.com/file

# Test HTTP endpoint
curl -I http://example.com
curl -X POST -d "data" http://example.com/api

# Network bandwidth
iftop
nethogs

# Packet capture
sudo tcpdump -i eth0
sudo tcpdump -i eth0 port 80
```

---

## Contributing

Feel free to contribute to this repository by:
1. Forking the repository
2. Creating a feature branch
3. Adding your commands or improvements
4. Submitting a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Maintained with ❤️ by the DevOps Community**
