FROM ubuntu:14.04
MAINTAINER Stefan Dang <stefan.dang@studium.uni-hamburg.de>

# Versions
ENV bamtools_version v2.3.0
#ENV sga_version v0.10.13
ENV bwa_version 0.7.8
ENV abyss_version 1.5.2
ENV samtools_version 1.1

# Install dependencies
RUN sudo apt-get update &&\
    sudo apt-get install -yqq \
      autoconf \
      automake \
      build-essential \
      cmake \
      git \
      libboost-all-dev \
      libopenmpi-dev \
      libncurses5-dev \
      libncursesw5-dev \
      libtool \
      sparsehash \
      wget \
      zlib1g-dev

# Build bamtools
RUN git clone -b $bamtools_version https://github.com/pezmaster31/bamtools.git bamtools
WORKDIR ./bamtools
RUN mkdir build && cd build && cmake .. && cd src && make install
WORKDIR ..

# Build sga
#RUN git clone -b $sga_version https://github.com/jts/sga.git sga
RUN git clone https://github.com/stepf/sga.git sga
WORKDIR ./sga
RUN cd src && ./autogen.sh && ./configure --with-bamtools=/bamtools && make && make install
WORKDIR ..

# Build bwa
RUN git clone -b $bwa_version https://github.com/lh3/bwa.git bwa
WORKDIR ./bwa
RUN make && cp bwa /usr/local/bin
WORKDIR ..

# Build art
WORKDIR ./art
RUN wget -qO- http://www.niehs.nih.gov/research/resources/assets/docs/artbinvanillaicecream031114linux64tgz.tgz | tar xz
RUN cd art_bin_VanillaIceCream && cp art_454 art_SOLiD art_illumina /usr/local/bin
WORKDIR ..

# Build Abyss
RUN git clone -b $abyss_version https://github.com/bcgsc/abyss.git
WORKDIR ./abyss
RUN ./autogen.sh && ./configure && make && make install
WORKDIR ..

# Build samtools
RUN wget -qO- \
    http://sourceforge.net/projects/samtools/files/samtools/$samtools_version/samtools-$samtools_version.tar.bz2/download \
    | tar -xj
WORKDIR ./samtools-$samtools_version
RUN make && make install
WORKDIR ..

# Set entrypoint
COPY ./sga_entrypoint.sh /sga_entrypoint.sh
RUN chmod +x /sga_entrypoint.sh
CMD ["/sga_entrypoint.sh"]
