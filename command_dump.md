ubuntu@ip-172-31-13-103:~/mlops-gitops$ history
    1  sudo apt update && sudo apt upgrade -y
    2  sudo apt install python3 python3-pip python3-venv git -y
    3  python3 --version
    4  pip --version
    5  pip3 --version
    6  python --version
    7  git clone https://github.com/CloudDevOpsHub/MLOPS-Project
    8  cd MLOPS-Project
    9  python3 -m venv .mlops
   10  source .mlops/bin/activate
   11  pip install --upgrade pip
   12  pip install -r requirements.txt
   13  python train.py
   14  ls
   15  uvicorn main:app --host 0.0.0.0 --port 8000
   16  sudo apt update && sudo apt install -y docker.io
   17  sudo systemctl enable docker
   18  docker -v
   19  curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl
   20  chmod +x kubectl
   21  sudo mv kubectl /usr/local/bin/
   22  kubectl version --client
   23  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   24  sudo apt install -y unzip
   25  sudo systemctl start docker
   26  docker --version
   27  sudo usermod -aG docker $USER
   28  newgrp docker
   29  kubectl get nodes
   30  kubectl get svc
   31  kubectl get deploy
   32  kubectl get ns
   33  kubectl get pods
   34  unzip awscliv2.zip
   35  aws --version
   36  sudo apt install awscli
   37  curl -sLO https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz
   38  tar -xzf eksctl_Linux_amd64.tar.gz
   39  sudo mv eksctl /usr/local/bin/
   40  eksctl version
   41  docker build -t it-career-api .
   42  ls
   43  cd MLOPS-Project
   44  ls
   45  docker build -t it-career-api .
   46  docker images
   47  docker login
   48  docker tag it-career-api rohit1k/it-career-api:latest
   49  docker push rohit1k/it-career-api:latest
   50  aws configure
   51  eksctl create cluster --name mlops-cluster --region ap-south-1b --nodegroup-name mlops-nodes --node-type t3.medium --nodes 2 --nodes-min 2 --nodes-max 3 --managed 
   52  eksctl create cluster --name mlops-cluster --region ap-south-1 --nodegroup-name mlops-nodes --node-type t3.medium --nodes 2 --nodes-min 2 --nodes-max 3 --managed 
   53  aws eks describe-cluster   --name mlops-cluster   --region ap-south-1
   54  kubectl get ns
   55  source kubectl-connect mlops-cluster
   56  kubectl get context
   57  kubectl current-context
   58  kubectl current context
   59  ls
   60  clear
   61  ls
   62  aws sts get-caller-identity
   63  aws eks get-token --cluster-name mlops-cluster --region ap-south-1
   64  kubectl config view --minify
   65  aws eks describe-cluster   --name mlops-cluster   --region ap-south-1
   66  kubectl version --client
   67  aws eks update-kubeconfig   --region ap-south-1   --name mlops-cluster
   68  kubectl get ns
   69  ls
   70  kubectl apply -f k8s-deploy.yml
   71  kubectl get ns
   72  kubectl get deployments
   73  kubectl get svc
   74  kubectl get pods
   75  kubectl get svc
   76  kubectl get deployments
   77  kubectl get svc
   78  kubectl get pods
   79  kubectl describe pod it-career-api-7bc68d6d69-p26bl
   80  kubectl get nodes
   81  aws eks describe-nodegroup   --cluster-name mlops-cluster   --nodegroup-name <nodegroup-name>   --region ap-south-1
   82  kubectl get nodes
   83  kubectl get deploy
   84  kubectl get svc
   85  kubectl get deploy
   86  eksctl create nodegroup   --cluster mlops-cluster   --region ap-south-1   --name workers   --node-type t3.medium   --nodes 2
   87  kubectl get nodes
   88  kubectl get deployments
   89  eksctl create nodegroup   --cluster mlops-cluster   --region ap-south-1   --name mlops-nodes   --node-type m7i-flex.large   --nodes 1   --nodes-min 1   --nodes-max 2   --managed
   90  kubectl get pods
   91  kubectl get deployments
   92  kubectl get ns
   93  kubectl get svc
   94  l
   95  cd MLOps-Project
   96  cd MLOps-Project/
   97  ls
   98  cd MLOps-Project
   99  cd MLOPS-Project
  100  ls
  101  kubectl delete it-career-api-service
  102  kubectl delete deployment it-career-api
  103  kubectl get ns
  104  kubectl get svc
  105  kubectl get deployments
  106  kubectl delete svc it-career-api-service
  107  ls
  108  kubectl apply -f k8s-deploy.yml
  109  kubectl get deploy
  110  kubectl get svc
  111  kubectl get pods
  112  kubectl get pods -w
  113  kubectl get deploy
  114  cat k8s-deploy.yml
  115  kubectl get svc
  116  kubectl create namespace argocd
  117  kubectl apply -n argocd   -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
  118  kubectl get pods -n argocd
  119  kubectl get svc -n argocd
  120  kubectl get pods -n argocd
  121  kubectl port-forward svc/argocd-server -n argocd 8080:443
  122  kubectl get pods -n argocd
  123  kubectl get nodes
  124  eksctl create nodegroup   --cluster mlops-cluster   --region ap-south-1   --name mlops-nodes   --node-type t3.micro   --nodes 1   --nodes-min 1   --nodes-max 1   --managed
  125  kubectl get nodes
  126  eksctl delete  nodegroup   --cluster mlops-cluster   --region ap-south-1   --name mlops-nodes   --node-type m7i-flex.large   --nodes 1   --nodes-min 1   --nodes-max 2   --managed
  127  kubectl get nodes
  128  kubectl delete k8s-deploy.yml
  129  kubectl get ns
  130  kubectl delete argocd
  131  kubectl delete ns argocd
  132  eksctl delete cluster --name mlops-cluster --region ap-south-1
  133  eksctl create cluster --name mlops-cluster1 --region ap-south-1 --nodegroup-name mlops-nodes --node-type m7i-flex.large --nodes 1 --nodes-min 1 --nodes-max 2 --managed 
  134  kubectl get nodes
  135  ls
  136  kubectl -f apply k8s-deploy.yml
  137  kubectl apply -f  k8s-deploy.yml
  138  kubectl get deploy
  139  kubectl get svc
  140  kubectl get pods
  141  kubectl get svc
  142  kubectl get deploy
  143  kubectl create namespace argocd
  144  kubectl apply -n argocd   -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
  145  helm repo add eks https://aws.github.io/eks-charts
  146  helm install aws-load-balancer-controller eks/aws-load-balancer-controller
  147  sudo apt install helm
  148  kubectl get pods -n argocd -w
  149  kubectl get pods -n argocd 
  150  kubectl patch svc argocd-server -n argocd   -p '{"spec": {"type": "LoadBalancer"}}'
  151  kubectl get svc -n argocd
  152  kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
  153  curl -sSL -o argocd https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
  154  chmod +x argocd
  155  sudo mv argocd /usr/local/bin/
  156  kubens
  157  sudo apt install kubectx
  158  kubectl get ns
  159  kubens argocd
  160  kubectl get pods
  161  kubectl get deployments
  162  kubectl get service
  163  argocd version
  164  argocd cluster add $(kubectl config current-context)
  165  argocd cluster list
  166  argocd login a2973e4473c154d4c91899f3fe593aca-1668799945.ap-south-1.elb.amazonaws.com   --username admin   --password BW6UmQ6itQ5cuEbB   --insecure
  167  argocd account get-user-info
  168  argocd cluster add $(kubectl config current-context)
  169  argocd cluster list
  170  mkdir mlops-gitops
  171  cd mlops-gitops
  172  git init
  173  mkdir -p apps/it-career-api/base
  174  mkdir -p apps/it-career-api/overlays/prod
  175  mkdir -p argocd/applications
  176  ls
  177  nano apps/it-career-api/base/deployment.yaml
  178  vi apps/it-career-api/base/service.yaml
  179  vi apps/it-career-api/base/kustomization.yaml
  180  vi apps/it-career-api/overlays/prod/kustomization.yaml
  181  nano argocd/applications/it-career-api.yaml
  182  vi argocd/applications/it-career-api.yaml
  183  git add .
  184  git commit -m "initial gitops setup"
  185  git config --global user.name "Rohit281k"
  186  git config --global user.email "rohitchaurasia280@gmail.com"
  187  git add .
  188  git commit -m "initial gitops setup"
  189  git branch -M main
  190  git remote add origin https://github.com/Rohit281k/mlops-gitops.git
  191  git push -u origin main
  192  git pull origin main --rebase
  193  git push -u origin main
  194  kubectl apply -f argocd/applications/it-career-api.yaml
  195  argocd app list
  196  kubectl get pods
  197  kubectl get svc
  198  kubectl get pods
  199  history
