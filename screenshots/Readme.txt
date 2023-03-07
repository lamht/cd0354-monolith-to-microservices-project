Git
https://github.com/lamht/cd0354-monolith-to-microservices-project

----
DockerHub
https://hub.docker.com/repository/docker/thanhlam00290/udagram-frontend/general
https://hub.docker.com/repository/docker/thanhlam00290/udagram-api-feed/general
https://hub.docker.com/repository/docker/thanhlam00290/udagram-api-user/general
https://hub.docker.com/repository/docker/thanhlam00290/udagram-reverseproxy/general

eksctl create cluster --name udacity-dev-project03-1 --region=us-east-1 --nodes-min=2 --nodes-max=3
aws eks update-kubeconfig   --region us-east-1   --name udacity-dev-project03
kubectl expose deployment reverseproxy --type=LoadBalancer --name=publicreverseproxy
kubectl expose deployment frontend --type=LoadBalancer --name=publicfrontend

kubectl autoscale deployment frontend --cpu-percent=50 --min=1 --max=10
kubectl autoscale deployment backend-feed --cpu-percent=50 --min=1 --max=10

aws eks update-kubeconfig --name udacity-dev-project03-1 --region=us-east-1

kubectl create secret generic env-secret --from-literal=db-username=postgres --from-literal=db-password=xxxx
kubectl create secret generic aws-secret --from-file=config=s3-permission.txt