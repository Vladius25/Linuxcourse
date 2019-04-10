FROM fedora

RUN dnf install -y -q vim openssh-server openssh-clients iproute bash nano ethtool freeipa-client iputils less sudo
RUN ssh-keygen -A
RUN sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
RUN usermod -p "\$6\$Cya6Q7UV\$r88j9s1.RxTaW.abzj4R9DKA4TZoAEnfTV7oVMvnknPer2t2QrMSdWb3UPeKSwNFH2RCJrtsXd0Cgn66NYJ1Q0" root

COPY task /root/

RUN for i in {1..20}; do mkdir -p /home/user$i; done
RUN echo "#! /bin/bash" > /bin/systemctl
RUN authselect select sssd --force > /dev/null
