******************FOR DOCKERFILE1***********************

# 📌 Task Brief – Docker Custom Image Creation & Runtime Configuration

## 🔹 Objective

create ec2, install nettools,jq docker

## 1️⃣ Created a Custom Dockerfile
use dockerfile1 create file on ec2 nano dockrfile.dev copy and paste
#build docker file
docker build -f dockerfile.dev .

#build with tag
docker build -t my-dev-image -f dockerfile.dev .

#build with tag and no cache
docker build -t my-dev-image -f dockerfile.dev . --no-cache
#run conatiner
docker run --rm -d app1 -p 8000:80 my-dev-image
docker ps
log in to app1
docker exec -it app1 bash
./terraform version


## 2️⃣ Used ARG for Dynamic Tool Versions

You defined:

```dockerfile
ARG T_VERSION='1.6.6'
ARG P_VERSION='1.8.0'
```

Then passed custom versions during build:

```bash
docker build -t kiran2361993/custom:v1 \
  --build-arg T_VERSION=1.5.6 \
  --build-arg P_VERSION=1.4.0 \
  -f dockerfile.dev .
```

🔹 This allows flexible version control at build time.

---

## 3️⃣ Built Docker Image

You built image using:

```bash
docker build -t my-dev-image -f dockerfile.dev .
```

Learned:

* Difference between tagged vs dangling images
* Importance of `-t` flag
* How `--no-cache` works

---

## 4️⃣ Ran Container with Environment Variables

You ran container with runtime environment variables:

```bash
docker run --rm -d --name app1 -p 8000:80 \
-e AWS_ACCESS_KEY_ID=hidden \
-e AWS_SECRET_ACCESS_KEY=hidden \
-e AWS_DEFAULT_REGION=us-east-1 \
kiran2361993/custom:v1
```

🔹 Learned:

* Difference between `ARG` (build time) and `ENV` (runtime)
* Environment variables can only be passed at container creation
* Containers are immutable

---

## 5️⃣ Accessed Running Container

You logged into container:

```bash
docker exec -it app1 bash
```

Verified:

* Terraform version
* Packer version
* AWS environment variables

---

You demonstrated:

✅ Custom Docker image creation
✅ Package installation inside container
✅ Build-time argument handling
✅ Runtime environment variable injection
✅ Container lifecycle management
✅ EC2 persistence behavior
✅ Understanding of Docker immutability


