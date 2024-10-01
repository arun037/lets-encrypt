steps for cert-manager using lets-encrypt

pre-requisites:

eks-cluster

cert-manager

route-53 hosted zone

ingress-nginx controller

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

step 1: install cert-manager to your eks cluster

kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.3/cert-manager.yaml

step 2: install ingress-nginx

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx	<Add Ingress NGINX repository>.

helm repo update	<Update Helm repositories>.

helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace --set-string controller.service.annotations."service\.beta\.kubernetes\.io/aws-load-balancer-type"="nlb"

kubectl get pods -n ingress-nginx

kubectl get svc -n ingress-nginx

step3: kubectl apply -f clusterissuer.yaml

step4: 
