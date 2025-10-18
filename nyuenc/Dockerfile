FROM almalinux:8

RUN dnf install -y dnf-plugins-core
RUN dnf install -y gcc-toolset-12 zip unzip make
RUN dnf install -y time
RUN dnf install -y valgrind
RUN dnf install -y strace

# Set up environment to use gcc from gcc-toolset-12
ENV PATH=/opt/rh/gcc-toolset-12/root/usr/bin:$PATH
ENV LD_LIBRARY_PATH=/opt/rh/gcc-toolset-12/root/usr/lib64:$LD_LIBRARY_PATH

# Default working dir and command
WORKDIR /
CMD ["/bin/bash"]
