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

export KOPS_STATE_STORE=s3://<bucket-name>

 kops create cluster --name mustafa.k8s.local --zones us-east-2a,us-east-2b --master-size c7i-flex.large --master-volume-size 30 --node-count 2 --node-volume-size 20 --node-size t3.micro --image=<ubuntu-ami-id>

kops update cluster --name mustafa.k8s.local --yes --admin

kubectl get nodes
