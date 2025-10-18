FROM rockylinux:8

RUN dnf install -y dnf-plugins-core
RUN dnf install -y gcc-toolset-12 zip unzip make
RUN dnf install -y time
RUN dnf install -y gdb
RUN dnf install -y valgrind
RUN dnf install -y strace
RUN dnf install -y xz

# Set up environment to use gcc from gcc-toolset-12
ENV PATH=/opt/rh/gcc-toolset-12/root/usr/bin:$PATH
ENV LD_LIBRARY_PATH=/opt/rh/gcc-toolset-12/root/usr/lib64:$LD_LIBRARY_PATH

# Default working dir and command
# Create a non-root user for VS Code remote
RUN useradd -m vscode && echo "vscode ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER vscode
WORKDIR /workspace
