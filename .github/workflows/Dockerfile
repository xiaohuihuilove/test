FROM centos:7.5.1804 
ENV container docker
 
RUN mkdir -p /home/admin  

WORKDIR /home/admin  
RUN cat /etc/redhat-release & hostname
RUN yum update -y -q
RUN yum install  -y -q wget net-tools sudo 
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
 
VOLUME [ "/sys/fs/cgroup" "/etc/kubernetes"]
EXPOSE 8080 22 6443 2379 2380 10250 10251 10252 10255
 CMD ["/usr/sbin/init"]
