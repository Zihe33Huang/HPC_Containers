

```
Bootstrap: docker
From: ubuntu:22.04

%files
   mpich-3.4.2.tar.gz /root/

%environment
    export SINGULARITY_MPICH_DIR=/usr

%post
    # Update the system and install necessary packages
    apt-get update && apt-get install -y --no-install-recommends \
        apt-utils \
        build-essential \
        curl \
        libcurl4-openssl-dev \
        libzmq3-dev \
        pkg-config \
        software-properties-common
    apt-get clean
    apt-get install -y dkms
    apt-get install -y autoconf automake build-essential numactl libnuma-dev autoconf automake gcc g++ git libtool

    apt-get -y update && DEBIAN_FRONTEND=noninteractive apt-get -y install build-essential libfabric-dev libibverbs-dev gfortran
    cd /root
    tar zxvf mpich-3.4.2.tar.gz && cd mpich-3.4.2
    echo "Configuring and building MPICH..."
    ./configure --prefix=/usr --with-device=ch4:ofi --disable-fortran    
    make -j8 install

```
