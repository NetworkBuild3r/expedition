FROM ubuntu:20.04

# Ensure that all interactions with package installation are non-interactive
ENV DEBIAN_FRONTEND=noninteractive

# Update and install necessary packages
RUN apt-get update && \
    apt-get -y install --no-install-recommends apt-transport-https lsb-core lsb-release net-tools netcat-openbsd sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Other commands
RUN touch /usr/bin/firewall-cmd && \
    chmod +x /usr/bin/firewall-cmd && \
    useradd -m expedition && \
    chmod 755 /root

# Copy setup files and set work directory
COPY ./setup /setup
WORKDIR /setup

# Set terminal environment variable
ENV TERM=xterm

# Run the setup script
RUN ./initSetup.sh

# Clean up
RUN rm -rf /setup /tmp/* /var/tmp/*

# Set work directory and copy start script
WORKDIR /
COPY start.sh /
CMD ["/start.sh"]
