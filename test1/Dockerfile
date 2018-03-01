FROM  centos:7
WORKDIR /tmp/k8s-1.9.0
ADD kubernetes.repo /etc/yum.repos.d/
RUN yum makecache 
#RUN yum install --downloadonly  --downloaddir=./  kubelet kubeadm kubectl
RUN yumdownloader kubelet kubeadm kubectl
RUN ls -al /tmp/k8s-1.9.0
