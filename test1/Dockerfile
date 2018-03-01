FROM  centos:7
WORKDIR /tmp/k8s-1.9.0
ADD kubernetes.repo /etc/yum.repos.d/
#RUN yum install -y –downloadonly –downloaddir=k8s-1.9.0 kubelet-1.9.0 kubeadm-1.9.0 kubectl-1.9.0
RUN yum install –downloadonly –downloaddir=./ kubelet kubeadm kubectl
RUN ls -al /tmp/k8s-1.9.0
