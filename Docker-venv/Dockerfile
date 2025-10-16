FROM ubuntu:24.04

RUN apt-get update && apt-get -y install openssh-server && apt install nano



FROM ubuntu:24.04
RUN apt-get update && apt-get install -y openssh-server sudo python3 python3-venv python3-pip iproute2 && rm -rf /var/lib/apt/lists/*
RUN useradd -m -s /bin/bash -G sudo -p "$(openssl passwd -6 ansible)" ansible && mkdir -p /home/ansible/.ssh /var/run/sshd && chown -R ansible:ansible /home/ansible/.ssh && chmod 700 /home/ansible/.ssh
RUN echo "ansible ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ansible && chmod 440 /etc/sudoers.d/ansible
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]


FROM ubuntu:24.04

RUN apt-get update && apt-get install -y openssh-server

RUN useradd -m -s /bin/bash ansible && echo 'ansible:ansible' | chpasswd && usermod -aG sudo ansible && echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]