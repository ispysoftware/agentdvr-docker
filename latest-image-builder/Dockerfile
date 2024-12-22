# Use DEBIAN BOOKWORM-SLIM
FROM debian:bookworm-slim

ARG DEBIAN_FRONTEND=noninteractive
ARG TZ=Asia/Dhaka

RUN mkdir /AgentDVR

COPY --chmod=555 dependency.sh /AgentDVR
COPY --chmod=555 setup.sh /AgentDVR
COPY --chmod=555 ffmpeg.sh /AgentDVR
COPY --chmod=555 banner.sh /AgentDVR
COPY --chmod=555 Agent.sh /AgentDVR
COPY --chmod=444 build-timestamp /AgentDVR

# Install dependencies
RUN bash /AgentDVR/dependency.sh

# Download/Install iSpy Agent DVR
RUN bash /AgentDVR/setup.sh

# Install ffmpeg
RUN bash /AgentDVR/ffmpeg.sh

#############################################################################
# 1. Install coturn
#############################################################################

RUN apt-get update && \
    apt-get install -y coturn && \
    rm -rf /var/lib/apt/lists/*

#############################################################################
# 2. Copy custom turnserver.conf into the container
#############################################################################
# You can create a separate turnserver.conf file with your desired config.
# An example turnserver.conf is shown below. Adjust paths as needed.

COPY turnserver.conf /etc/turnserver.conf

#############################################################################
# 3. Enable and configure coturn
#############################################################################
# The default Debian package for coturn uses /etc/default/coturn to enable/disable
# the service. We will enable it, but in Docker, we often run the turnserver
# manually in the foreground with --no-daemon so it runs in the container.

RUN sed -i 's/#TURNSERVER_ENABLED=.*/TURNSERVER_ENABLED=1/' /etc/default/coturn

#############################################################################
# 4. Clean up
#############################################################################

RUN apt-get -y --purge --allow-remove-essential remove unzip wget && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /AgentDVR/dependency.sh && \
    rm -rf /AgentDVR/setup.sh && \
    rm -rf /AgentDVR/source.sh && \
    rm -rf /AgentDVR/update.sh && \
    rm -rf /AgentDVR/ffmpeg.sh

#############################################################################
# 5. Expose the necessary ports
#############################################################################

# Main UI port for Agent DVR
EXPOSE 8090

# HTTPS port (if you need it)
EXPOSE 443

# STUN (UDP) – usually 3478
EXPOSE 3478/udp

# TURN can also listen on TCP or TLS at 3479 if you wish
# EXPOSE 3479/tcp

# TURN relay ports (UDP range)
EXPOSE 50000-50100/udp

#############################################################################
# 6. Run both coturn and Agent DVR
#############################################################################
# We must start coturn in the foreground (i.e., with --no-daemon)
# so that Docker keeps it running. We'll start Agent DVR afterward.
#
# NOTE: Docker containers have a single "PID 1" process. We combine both
# by running turnserver in the background (with &) then exec Agent.sh.

CMD ["/bin/bash", "-c", "turnserver -c /etc/turnserver.conf --no-daemon & exec /AgentDVR/Agent.sh"]
