FROM debian:bullseye

# Install developer tools and dependencies
RUN apt-get update && apt-get install -y \
        build-essential \
        gdb \
        valgrind \
        git \
        vim \
        man \
        manpages \
        less \
        zip \
        strace \
        procps \
        psmisc \
        diffutils \
        time

# Link cat, echo, grep, ps from /bin to /usr/bin
RUN ln -s /bin/cat /usr/bin/cat && \
    ln -s /bin/echo /usr/bin/echo && \
    ln -s /bin/grep /usr/bin/grep && \
    ln -s /bin/ps /usr/bin/ps

# Create a non-root user for VS Code remote
RUN useradd -m vscode && echo "vscode ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER vscode
WORKDIR /workspace
