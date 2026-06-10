# 🚀 End-to-End MLOps Deployment on AWS EKS using Argo CD (GitOps)

This project demonstrates a complete **production-style MLOps deployment pipeline** using:

- AWS EKS (Kubernetes cluster)
- kubectl (Kubernetes CLI)
- Argo CD (GitOps continuous delivery)
- Dockerized application deployment
- AWS LoadBalancer for external access

---

# 🧠 Architecture Overview
   
             GitHub Repository (GitOps)
                      ↓
             Argo CD (Deployment Controller)
                      ↓
             AWS EKS Cluster (Kubernetes)
                      ↓
             Worker Nodes (EC2 Instances)
                      ↓
             Pods (Application Containers)
                      ↓
            AWS LoadBalancer (Public Access)


1. Create EKS cluster

              eksctl create cluster \
               --name mlops-cluster \
               --region ap-south-1 \
               --nodegroup-name mlops-nodes \
               --node-type m7i-flex.large \
               --nodes 1 \
               --nodes-min 1 \
               --nodes-max 2 \
               --managed

3. Verify cluster

            kubectl get nodes

4. Deploy Sample Application (Before Argo CD)

           kubectl create deployment test --image=nginx
           kubectl expose deployment test --type=LoadBalancer --port=80

           kubectl get svc

5. Install Argo CD
   
           kubectl create namespace argocd
           kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

6. Expose Argo CD UI

         kubectl patch svc argocd-server -n argocd \
           -p '{"spec": {"type": "LoadBalancer"}}'
   
    Get URL:

          kubectl get svc -n argocd

7. Get Argo CD Admin Password

         kubectl -n argocd get secret argocd-initial-admin-secret \
           -o jsonpath="{.data.password}" | base64 -d

   Login credentials:
          Username: admin
          Password: (from above command)

8. Login to Argo CD CLI

        argocd login <ARGOCD_LB_URL> \
          --username admin \
          --password <PASSWORD> \
          --insecure
   
9. Connect EKS Cluster to Argo CD

         argocd cluster add $(kubectl config current-context)
   
   verify:

         argocd cluster list

11. Repository Structure
    
              mlops-gitops/
              │
              ├── apps/
              │   └── it-career-api/
              │       ├── base/
              │       │   ├── deployment.yaml
              │       │   ├── service.yaml
              │       │   └── kustomization.yaml
              │       │
              │       └── overlays/
              │           └── prod/
              │               └── kustomization.yaml
              │
              └── argocd/
                  └── applications/
                      └── it-career-api.yaml

12. Example Kubernetes Deployment

              apiVersion: apps/v1
              kind: Deployment
              metadata:
                name: it-career-api
              spec:
                replicas: 2
                selector:
                  matchLabels:
                    app: it-career-api
                template:
                  metadata:
                    labels:
                      app: it-career-api
                  spec:
                    containers:
                    - name: it-career-api
                      image: nginx
                      ports:
                      - containerPort: 80
    
13. Service Definition

                apiVersion: v1
                kind: Service
                metadata:
                  name: it-career-api-service
                spec:
                  selector:
                    app: it-career-api
                  ports:
                    - port: 80
                      targetPort: 80
                  type: LoadBalancer


14. Argo CD Application

                apiVersion: argoproj.io/v1alpha1
                kind: Application
                metadata:
                  name: it-career-api
                  namespace: argocd
                spec:
                  project: default
                
                  source:
                    repoURL: https://github.com/YOUR_USERNAME/mlops-gitops.git
                    targetRevision: main
                    path: apps/it-career-api/overlays/prod
                
                  destination:
                    server: https://kubernetes.default.svc
                    namespace: default
                
                  syncPolicy:
                    automated:
                      prune: true
                      selfHeal: true

15. Push GitOps Repo

                  git init
                  git add .
                  git commit -m "initial gitops setup"
                  git branch -M main
                  git remote add origin <YOUR_REPO_URL>
                  git push -u origin main

16. Access Applications

                  Argo CD UI:
                        http://<ARGOCD-LOADBALANCER>
                  Application:
                        http://<APP-LOADBALANCER>

17. 🧠 Key Concepts Learned
      1. Kubernetes Cluster
      
      Manages container workloads
      
      2. Worker Nodes
      
      Run actual pods (required for everything)
      
      3. Argo CD
      
      Automates deployments using GitOps
      
      4. GitOps
      
      Git = single source of truth for deployments    
    
   
   

           
        
