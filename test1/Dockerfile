FROM  centos:7
WORKDIR /tmp
RUN yum install -y –downloadonly –downloaddir=k8s-1.9.0 kubelet-1.9.0 kubeadm-1.9.0 kubectl-1.9.0
RUN ls -al /tmp/k8s-1.9.0