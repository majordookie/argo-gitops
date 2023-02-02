```
kind create cluster --config .\kind-config.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
helm repo add argo https://argoproj.github.io/argo-helm
kubectl create namespace argocd
helm install --namespace argocd argo argo/argo-cd
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
kubectl port-forward svc/argo-argocd-server -n argocd 8080:443
helm repo add couchbase https://couchbase-partners.github.io/helm-charts/
```