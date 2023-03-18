FROM amazonlinux:2

# install amazon-linux-extras install
RUN amazon-linux-extras install -y

# yum update & install
RUN yum update -y \
    && yum install \
        systemd \
        tar \
        unzip \
        sudo \
        git \
        mariadb \
        -y

# install aws cli v2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && sudo ./aws/install

# python install (3.8)
RUN yum install -y gcc zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel make \
    && curl -LO https://www.python.org/ftp/python/3.8.16/Python-3.8.16.tgz \
    && tar zxvf Python-3.8.16.tgz \
    && cd Python-3.8.16 \
    && ./configure --prefix=/usr/local/python \
    && make \
    && make install \
    && ln -s /usr/local/python/bin/python3 /usr/local/bin/python \
    && ln -s /usr/local/python/bin/pip3 /usr/local/bin/pip

# create user
RUN useradd "ec2-user" && echo "ec2-user ALL=NOPASSWD: ALL" >> /etc/sudoers

# init
CMD ["/sbin/init"]