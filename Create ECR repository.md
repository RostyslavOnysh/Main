# Create an ECR Repository:
```bash
aws ecr create-repository --repository-name <name> --region eu-west-1
```

# Tag your Docker image:
```bash
docker tag readers-paradise:latest 963746698577.dkr.ecr.eu-west-1.amazonaws.com/readers-paradise:latest
```
# Push the tagged image to the repository:
```bash
docker push 963746698577.dkr.ecr.eu-west-1.amazonaws.com/readers-paradise:latest
```
