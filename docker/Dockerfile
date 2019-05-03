FROM scratch
ADD centos-7-x86_64-docker.tar.xz /

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20190305"

ADD environment.yml /usr/local/

RUN yum -y update \
    && yum -y install curl bzip2 which git openssh java-1.8.0-openjdk \
    && curl -sSL https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -bfp /usr/local/ \
    && rm -rf /tmp/miniconda.sh \
    && conda update conda \
    && conda env create -f /usr/local/environment.yml \
    && conda clean --all --yes \
    && conda init bash \
    && rpm -e --nodeps curl bzip2 \
    && yum clean all

CMD ["/bin/bash"]
