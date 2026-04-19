# kops-installation-

**Kops Cluster Creation commands:**

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install


curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl

mv kubectl /usr/local/bin/

curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64

chmod +x kops

sudo mv kops /usr/local/bin/kops


aws s3 ls


aws s3 mb s3://<bucket-name>

export KOPS_STATE_STORE=s3://s3-kops-b

 kops create cluster --name reddy.k8s.local --zones us-east-1c,us-east-1b --master-size t2.medium --master-volume-size 30 --node-count 2 --node-volume-size 20 --node-size t2.small --image=ami-0ec10929233384c7f

kops update cluster --name reddy.k8s.local --yes --admin

kubectl get nodes

**Kuster deletion**
kops delete cluster reddy.k8s.local --yes
