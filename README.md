# First build the docker image that is compatible for linux - arm/amd64 issue as earlier image was generated on mac

    1. gcloud auth login

# Set the correct project
    2. gcloud config set project myapp-477208

# Configure Docker to push to GCR
    3. gcloud auth configure-docker

    4. docker buildx build --platform linux/amd64,linux/arm64 -t gcr.io/myapp-477208/product-service:latest --push .

# After this create namespace, secret, pv, pvc, mysql-service,statefulset, web-deploymment,service, etc.

# Apply all the objects in order - namespace & secret, PV, PVC, mysql service/statefulset, then web:

    1. kubectl apply -f namespace.yaml
    2. kubectl apply -n myapp -f mysql-secret.yaml

# Before creating mysql-pv.yaml, created a disk in GKE

    3. kubectl apply -f mysql-pv.yaml
    4. kubectl apply -n myapp -f mysql-pvc.yaml

    5. kubectl apply -n myapp -f mysql-service.yaml
    6. kubectl apply -n myapp -f mysql-statefulset.yaml

    7. kubectl apply -n myapp -f web-deployment.yaml
    8. kubectl apply -n myapp -f web-service.yaml

# To Check the status of all the kubernetes objects:

    1. kubectl -n myapp get pv,pvc
    2. kubectl -n myapp get pods,sts,deploy,svc
    3. kubectl -n myapp describe pod <mysql-pod-name>   # for logs/errors
    4. kubectl -n myapp logs deployment/restapi --tail=100




