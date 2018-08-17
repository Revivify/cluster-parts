FROM amazonlinux:2
RUN yum install -q -y gcc libstdc++-devel gcc-c++ fuse fuse-devel curl-devel libxml2-devel mailcap make automake openssl-devel git
RUN git clone https://github.com/s3fs-fuse/s3fs-fuse && cd s3fs-fuse && ./autogen.sh && ./configure --prefix=/out --with-openssl && make && make install
FROM amazonlinux:2
RUN yum install -q -y fuse fuse-libs
ENV TINI_VERSION v0.18.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini 
COPY --from=0 /out /usr

