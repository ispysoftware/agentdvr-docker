<h1>iSpy Agent DVR multi-arch image</h1>
<img alt="ispyagentdvr" src="https://www.ispyconnect.com/img/agent.webp">
<p>Official Agent DVR image. Website: <a href="https://www.ispyconnect.com" rel="nofollow noopener">https://www.ispyconnect.com</a>
</p>
<p align="center">
  <a href="https://www.gnu.org/licenses/gpl-3.0"><img alt="License: GPLv3" src="https://img.shields.io/badge/License-GPLv3-blue.svg"></a>
  <a href="https://hub.docker.com/r/ispysoftware/agentdvr"><img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/ispysoftware/agentdvr.svg"></a>
  <a href="https://hub.docker.com/r/ispysoftware/agentdvr"><img alt="Docker Stars" src="https://img.shields.io/docker/stars/ispysoftware/agentdvr.svg"></a>
  <a href="https://ghcr.io/ispysoftware/agentdvr"><img alt="GHCR" src="https://img.shields.io/badge/GHCR-ghcr.io%2Fispysoftware%2Fagentdvr-blue"></a>
  <a href="https://hub.docker.com/r/ispysoftware/agentdvr"><img alt="Platforms" src="https://img.shields.io/badge/Platforms-amd64%20%7C%20arm64%20%7C%20arm%2Fv7-lightgrey"></a>
  <a href="https://github.com/ispysoftware/agentdvr-docker/stargazers"><img alt="GitHub Stars" src="https://img.shields.io/github/stars/ispysoftware/agentdvr-docker"></a>
  <a href="https://github.com/ispysoftware/agentdvr-docker/forks"><img alt="GitHub Forks" src="https://img.shields.io/github/forks/ispysoftware/agentdvr-docker"></a>
  <a href="https://github.com/ispysoftware/agentdvr-docker/issues"><img alt="GitHub Issues" src="https://img.shields.io/github/issues/ispysoftware/agentdvr-docker"></a>
  <a href="https://github.com/ispysoftware/agentdvr-docker/commits/main"><img alt="Last Commit" src="https://img.shields.io/github/last-commit/ispysoftware/agentdvr-docker.svg"></a>
</p>
<p>This official image is based on the community image originally created and maintained by <a href="https://github.com/MekayelAnik">MD. Mekayel Anik</a>, whose community build remains available at <a href="https://hub.docker.com/r/mekayelanik/ispyagentdvr">mekayelanik/ispyagentdvr</a>.</p>
<h2>Supported architectures</h2>
<table>
  <thead>
    <tr>
      <th align="center">Architecture</th>
      <th align="center">Available</th>
      <th>Tag</th>
       <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">x86-64</td>
      <td align="center">✅</td>
      <td>amd64-&lt;version tag&gt;</td>
      <td>Tested and working</td>
    </tr>
    <tr>
      <td align="center">arm64</td>
      <td align="center">✅</td>
      <td>arm64v8-&lt;version tag&gt;</td>
      <td>Tested and working</td>
    </tr>
    <tr>
      <td align="center">armhf</td>
      <td align="center">✅</td>
      <td>arm32v7-&lt;version tag&gt;</td>
      <td>Tested and working (4.8.2.0 and newer)</td>
    </tr>
  </tbody>
</table>
<h2>Announcements</h2>
<ul>
<li><strong>Directory structure:</strong> the application directory has reverted to <code>/AgentDVR</code> (previously <code>/home/agentdvr/AgentDVR</code>). Make sure your volume mappings reflect this, particularly in unRAID, Synology and other GUI-based container managers.</li>
<li><strong>Base image:</strong> the image is now based on Debian Trixie.</li>
<li><strong>Image compression:</strong> images use ZSTD compression to reduce size and bandwidth. Version 6.5.7.0 and later require Docker Engine 23.0+ (or Podman Machine v5.1+).</li>
<li><strong>WebRTC port range:</strong> the media port range has changed from <code>50000-50010</code> to <code>50000-50100</code>. Update the range in your Docker CLI command or Compose file accordingly.</li>
<li><strong>armhf:</strong> for ARM 32-bit devices, use version 4.8.2.0 or newer.</li>
<li><strong>GPU acceleration:</strong> hardware-accelerated encode/decode requires version 5.3.5.0 or newer.</li>
<li><strong>Beta images</strong> are for testing only and should not be used in production environments.</li>
<li>Review the <a href="https://www.ispyconnect.com/producthistory?productid=27" rel="nofollow noopener">release history</a> before pinning older tags.</li>
</ul>

<table>
  <thead>
    <tr>
      <th align="center">Tag</th>
      <th align="center">Available</th>
      <th>Description</th>
       <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">stable</td>
      <td align="center">✅</td>
      <td>The most recent release that has remained current for at least 5 days</td>
      <td>Recommended for production use</td>
    </tr>
    <tr>
      <td align="center">latest</td>
      <td align="center">✅</td>
      <td>The most recent release</td>
      <td>Tested and working</td>
    </tr>
    <tr>
      <td align="center">beta</td>
      <td align="center">⚠️</td>
      <td>The current beta release</td>
      <td>For testing only. Back up your configuration first; not recommended for production use</td>
    </tr>
    <tr>
      <td align="center">7.9.2.0</td>
      <td align="center">✅</td>
      <td>Pinned release 7.9.2.0</td>
      <td>Tested and working</td>
    </tr>
    <tr>
      <td align="center">7.9.3.0-beta</td>
      <td align="center">⚠️</td>
      <td>Beta release 7.9.3.0</td>
      <td>For testing only. Back up your configuration first; not recommended for production use</td>
    </tr>
  </tbody>
</table>
<h2>Running the image</h2>
<h3>docker-compose (recommended, <a href="https://docs.docker.com/compose/" rel="nofollow noopener">docs</a>) </h3>
<pre><code>---
services:
  ispyagentdvr:
    image: ispysoftware/agentdvr:latest
    container_name: ispyagentdvr
    environment:
      - PUID=1000
      - PGID=1000
      - AGENTDVR_WEBUI_PORT=8090
      - TZ=Europe/London
    volumes:
      - /path/to/config:/AgentDVR/Media/XML
      - /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media
      - /path/to/models:/AgentDVR/Media/Models
      - /path/to/commands:/AgentDVR/Commands
    ports:
      - 8090:8090
      - 3478:3478/udp
      - 50000-50100:50000-50100/udp
    restart: unless-stopped
</code></pre>

<p><strong>Note:</strong> on Raspberry Pi and other low-power ARM boards, allow around 30 seconds after deployment before opening the web UI, then refresh if needed. With many cameras configured, startup can take longer.</p>

<h3>docker cli ( <a href="https://docs.docker.com/engine/reference/commandline/cli/" rel="nofollow noopener">docs</a>) </h3>
<pre><code>docker run -d \
  --name=ispyagentdvr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e AGENTDVR_WEBUI_PORT=8090 \
  -e TZ=Europe/London \
  -p 8090:8090 \
  -p 3478:3478/udp \
  -p 50000-50100:50000-50100/udp \
  -v /path/to/config:/AgentDVR/Media/XML \
  -v /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media \
  -v /path/to/models:/AgentDVR/Media/Models \
  -v /path/to/commands:/AgentDVR/Commands \
  --restart unless-stopped \
  ispysoftware/agentdvr:latest
</code></pre>
<h3>Dedicated local IP using MACVLAN ( <a href="https://docs.docker.com/network/macvlan/" rel="nofollow noopener">docs</a>) </h3>
<pre><code>---
services:
  ispyagentdvr:
    image: ghcr.io/ispysoftware/agentdvr:latest
    container_name: ispyagentdvr
    environment:
      - PUID=1000
      - PGID=1000
      - AGENTDVR_WEBUI_PORT=8090
      - TZ=Europe/London
    volumes:
      - /path/to/config:/AgentDVR/Media/XML
      - /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media
      - /path/to/models:/AgentDVR/Media/Models
      - /path/to/commands:/AgentDVR/Commands
    ports:
      - 8090:8090
      - 3478:3478/udp
      - 50000-50100:50000-50100/udp
    restart: unless-stopped
    hostname: ispyagentdvr
    domainname: local
    mac_address: AB-BC-C0-D1-E2-EF
    networks:
      macvlan-1:
        ipv4_address: 192.168.2.12
networks:
  macvlan-1:
    name: macvlan-1
    external: True</code></pre>
<p>To use MACVLAN, set valid values for <code>mac_address</code>, <code>ipv4_address</code>, <code>subnet</code>, <code>ip_range</code> and <code>gateway</code>. Access the web UI at <code>http://ipv4_address:8090</code>.</p>
<h2>GPU hardware acceleration (5.3.5.0 and newer)</h2>
<p>Hardware-accelerated encode/decode requires image version 5.3.5.0 or newer, and the GPU render devices must be passed through to the container as shown below. If you run into problems, please open an issue on this image's GitHub repository (linked at the bottom of this page).</p>
<h3>docker-compose (recommended, <a href="https://docs.docker.com/compose/" rel="nofollow noopener">docs</a>) </h3>
<pre><code>---
services:
  ispyagentdvr:
    image: ghcr.io/ispysoftware/agentdvr:latest
    container_name: ispyagentdvr
    environment:
      - PUID=1000
      - PGID=1000
      - AGENTDVR_WEBUI_PORT=8090
      - TZ=Europe/London
    volumes:
      - /path/to/config:/AgentDVR/Media/XML
      - /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media
      - /path/to/models:/AgentDVR/Media/Models
      - /path/to/commands:/AgentDVR/Commands
    ports:
      - 8090:8090
      - 3478:3478/udp
      - 50000-50100:50000-50100/udp
    restart: unless-stopped
</code></pre>

<h3>docker cli ( <a href="https://docs.docker.com/engine/reference/commandline/cli/" rel="nofollow noopener">docs</a>) </h3>
<pre><code>docker run -d \
  --name=ispyagentdvr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e AGENTDVR_WEBUI_PORT=8090 \
  -e TZ=Europe/London \
  -p 8090:8090 \
  -p 3478:3478/udp \
  -p 50000-50100:50000-50100/udp \
  -v /path/to/config:/AgentDVR/Media/XML \
  -v /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media \
  -v /path/to/models:/AgentDVR/Media/Models \
  -v /path/to/commands:/AgentDVR/Commands \
  --restart unless-stopped \
  ispysoftware/agentdvr:latest</code></pre>
<h3>Nvidia GPUs</h3>
<p>Install the latest Nvidia drivers and the <a href="https://github.com/NVIDIA/nvidia-container-toolkit" rel="nofollow noopener">Nvidia Container Toolkit</a> on the host. The image already sets the environment variables needed to expose the GPU's capabilities.</p>
<p>With the toolkit installed, recreate the container with the Nvidia runtime (<code>--runtime=nvidia</code>) and add <code>-e NVIDIA_VISIBLE_DEVICES=all</code>. This can also be set to a specific GPU's UUID, which you can find with <code>nvidia-smi --query-gpu=gpu_name,gpu_uuid --format=csv</code>. The Nvidia runtime mounts the GPU and drivers from the host into the container automatically.</p>
<p><strong>CUDA AI object detection:</strong> the image ships video hardware acceleration only. For GPU object detection (CUDA + cuDNN), build a small overlay image — see <a href="https://github.com/ispysoftware/agentdvr-docker/blob/main/CUDA-ACCELERATION.md" rel="nofollow noopener">CUDA-ACCELERATION.md</a>.</p>
<h3>AMD GPUs and iGPUs</h3>
<p>Add the following to your Compose file or CLI command respectively:</p>
<p><strong>docker compose</strong></p>
<pre><code>devices:
    - /dev/dri/renderD128:/dev/dri/renderD128
    - /dev/dri/card0:/dev/dri/card0
    - /dev/kfd:/dev/kfd</code></pre>
<p><strong>docker cli</strong></p>
<pre><code>--device /dev/dri/renderD128:/dev/dri/renderD128 --device /dev/dri:/dev/dri/card0 --device /dev/kfd:/dev/kfd</code></pre>
<h3>Intel GPUs and iGPUs</h3>
<p>Add the following to your Compose file or CLI command respectively:</p>
<p><strong>docker compose</strong></p>
<pre><code>devices:
    - /dev/dri/renderD128:/dev/dri/renderD128
    - /dev/dri/card0:/dev/dri/card0</code></pre>
<p><strong>docker cli</strong></p>
<pre><code>--device /dev/dri/renderD128:/dev/dri/renderD128 --device /dev/dri/card0:/dev/dri/card0</code></pre>

<h3>Rockchip integrated VPUs</h3>
<pre><code>docker run -d \
  --name=ispyagentdvr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e AGENTDVR_WEBUI_PORT=8090 \
  -e TZ=Europe/London \
  -p 8090:8090 \
  -p 3478:3478/udp \
  -p 50000-50100:50000-50100/udp \
  -v /path/to/config:/AgentDVR/Media/XML \
  -v /path/to/recordings:/AgentDVR/Media/WebServerRoot/Media \
  -v /path/to/models:/AgentDVR/Media/Models \
  -v /path/to/commands:/AgentDVR/Commands \
  --restart unless-stopped \
`for dev in dri dma_heap mali0 rga mpp_service \
   iep mpp-service vpu_service vpu-service \
   hevc_service hevc-service rkvdec rkvenc vepu h265e ; do \
  [ -e "/dev/$dev" ] && echo " --device /dev/$dev"; \
 done` 
  ispysoftware/agentdvr:latest</code></pre>
<h2>Parameters</h2>
<p>Parameters are separated by a colon and indicate <code>&lt;external&gt;:&lt;internal&gt;</code>. For example, <code>-p 8090:80</code> exposes port <code>80</code> inside the container on host port <code>8090</code>.</p>
<table>
  <thead>
    <tr>
      <th align="center">Parameter</th>
      <th>Function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <code>-p 8090</code>
      </td>
      <td>Web UI port</td>
    </tr>
    <tr>
      <td align="center">
        <code>-p 3478/udp</code>
      </td>
      <td>TURN server port, used for WebRTC connection setup</td>
    </tr>
    <tr>
      <td align="center">
        <code>-p 50000-50100/udp</code>
      </td>
      <td>WebRTC media ports, allocated as needed</td>
    </tr>
    <tr>
      <td align="center">
        <code>-e PUID=1000</code>
      </td>
      <td>User ID - see User / Group Identifiers below</td>
    </tr>
    <tr>
      <td align="center">
        <code>-e PGID=1000</code>
      </td>
      <td>Group ID - see User / Group Identifiers below</td>
    </tr>
    <tr>
      <td align="center">
        <code>-e TZ=Europe/London</code>
      </td>
      <td>Timezone, from the <a href="https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List" rel="nofollow noopener">tz database</a></td>
    </tr>
    <tr>
      <td align="center">
        <code>-e AGENTDVR_WEBUI_PORT=8090</code>
      </td>
      <td>Port the web UI listens on inside the container</td>
    </tr>
    <tr>
      <td align="center">
        <code>-v /AgentDVR/Media/XML</code>
      </td>
      <td>Configuration files</td>
    </tr>
    <tr>
      <td align="center">
        <code>-v /AgentDVR/Media/WebServerRoot/Media</code>
      </td>
      <td>Recordings</td>
    </tr>
    <tr>
      <td align="center">
        <code>-v /AgentDVR/Media/Models</code>
      </td>
      <td>AI model files</td>
    </tr>
    <tr>
      <td align="center">
        <code>-v /AgentDVR/Commands </code>
      </td>
      <td>Custom commands</td>
    </tr>
  </tbody>
</table>
<h2>User / Group Identifiers</h2>
<p>When using volumes (<code>-v</code> flags), permission issues can arise between the host and the container. To avoid this, specify the user and group the container should run as with <code>PUID</code> and <code>PGID</code>, and make sure any volume directories on the host are owned by that user.</p>
<p>In the examples above <code>PUID=1000</code> and <code>PGID=1000</code>. To find yours, run <code>id username</code>:</p>
<pre><code>$ id username
uid=1000(docker user) gid=1000(docker group) groups=1000(docker group)</code></pre>
<h2>Documentation</h2>
<p>The Agent DVR user guide is available at <a href="https://www.ispyconnect.com/docs/agent/about" rel="nofollow noopener">https://www.ispyconnect.com/docs/agent/about</a>.</p>
<h2>Non-host networking</h2>
<p>When not using host networking, the UDP ports listed in the examples must be published for remote viewing to work.</p>
<p>The web UI is available at <code>http://&lt;container ip&gt;:8090</code> (or <code>http://ipv4_address:8090</code> with MACVLAN).</p>
<h2>Updating</h2>
<h3>Via Docker Compose (recommended)</h3>
<ul>
  <li>Update all images: <code>docker compose pull</code>
    <ul>
      <li>or update a single image: <code>docker compose pull ispyagentdvr</code>
      </li>
    </ul>
  </li>
  <li>Let compose update all containers as necessary: <code>docker compose up -d</code>
    <ul>
      <li>or update a single container (recommended): <code>docker compose up -d ispyagentdvr</code>
      </li>
    </ul>
  </li>
  <li>Remove old unused images: <code>docker image prune</code>
  </li>
</ul>
<h3>Via Docker Run</h3>
<ul>
  <li>Update the image: <code>docker pull ispysoftware/agentdvr:latest</code>
  </li>
  <li>Stop the running container: <code>docker stop ispyagentdvr</code>
  </li>
  <li>Delete the container: <code>docker rm ispyagentdvr</code>
  </li>
  <li>Recreate the container with the same docker run parameters as before (if <code>/AgentDVR/Media/XML</code> is mapped to a host folder, your settings are preserved) </li>
  <li>Remove old unused images: <code>docker image prune</code>
  </li>
</ul>
<h3>Via <a href="https://containrrr.dev/watchtower/" rel="nofollow noopener">Watchtower</a> (use only if you no longer have the original run parameters)</h3>
<ul>
  <li>
    <p>Pull the latest image and recreate the container with the same environment variables in one run:</p>
    <pre>
<code>docker run --rm \
-v /var/run/docker.sock:/var/run/docker.sock \
containrrr/watchtower\
--run-once ispyagentdvr</code></pre>
  </li>
  <li>
    <p>Remove old unused images: <code>docker image prune</code>
    </p>
  </li>
</ul>
<h3>Update notifications</h3>
<ul>
  <li><a href="https://crazymax.dev/diun/" rel="nofollow noopener">Diun</a> can notify you when a new image is available. Tools that update containers unattended are not recommended for a surveillance system.</li>
</ul>
<h2>Migration notes</h2>
<p>If you used the old separate audio and video volumes, move their contents into the new media folder before starting the container again:</p>
<pre>
<code>mkdir -p /ispyagentdvr/media/old && \
mv /path/to/recordings/audio /ispyagentdvr/media/old && \
mv /path/to/recordings/video /ispyagentdvr/media/old</code></pre>


<h2>Notes</h2>
<p><strong>Audio playback on Linux hosts:</strong> if action sounds do not play through the host's speakers (Debian/Ubuntu etc.), add the following to your Compose file:</p>
<pre><code>    group_add:
        - audio
    devices:
        - /dev/snd:/dev/snd
</code></pre>
<p><strong>ARM boards:</strong> Raspberry Pi 4 and newer may support limited hardware acceleration with the right host setup. Performance varies; if you find a reliable VAAPI/VPU configuration, share it on GitHub and it can be documented with credit.</p>
<p><strong>Before submitting an issue:</strong></p>
  <ul>
    <li>Update Docker Engine to the latest available version, especially on macOS, and check whether the issue persists.
    </li>
    <li>Check <code>&lt;agent-ip&gt;:&lt;port&gt;/logs.html</code> for errors.
    </li>
    <li>On Raspberry Pi 5, use Ubuntu or Ubuntu Server as the host OS. A Debian bug currently breaks Agent DVR (and other .NET applications) on the Pi 5; other Raspberry Pi models are not affected at the time of writing.
    </li>
    <li>Include your Compose file or docker run command and the relevant <code>logs.html</code> output in the report.
    </li>
  </ul>

<p><strong>Version history</strong></p>
<ul>
<li><strong>7.2.0.0:</strong> Breaking: a new volume mapping is required for persistent AI model storage: <code>/AgentDVR/Media/Models</code></li>
<li><strong>6.6.2.0:</strong> Breaking: directory structure reverted to <code>/AgentDVR</code> from <code>/home/agentdvr/AgentDVR</code>. Take particular care to apply this change in unRAID, Synology and other GUI-based container managers</li>
<li><strong>6.6.2.0:</strong> Base image changed to Debian Trixie from Bookworm</li>
<li><strong>6.6.2.0:</strong> Updated Intel driver to 25.31.34666.3 and AMD Mesa driver to 25.2.2-1</li>
<li><strong>6.6.2.0:</strong> armhf builds switched to FFmpeg from Debian SID after Jellyfin dropped armhf support</li>
<li><strong>6.5.7.0:</strong> Breaking: ZSTD compression applied to reduce image size and bandwidth. Requires Docker Engine 23.0+ (or Podman Machine v5.1+)</li>
<li><strong>6.3.4.0:</strong> Updated Intel GPU driver to Compute Runtime 25.18.33578.6, AMD Mesa driver to 25.0.7-1 and jellyfin-ffmpeg to 7.1.1-6</li>
<li><strong>6.0.9.0:</strong> Updated Intel GPU driver and jellyfin-ffmpeg to 7.0.2-9</li>
<li><strong>6.0.1.0:</strong> Added driver support for Intel Battlemage GPUs</li>
<li><strong>5.8.4.0:</strong> Breaking: configuration file format changed from XML to JSON</li>
<li><strong>5.8.1.0:</strong> FFmpeg updated from 6.0.1 to 7.0.2</li>
<li><strong>5.8.1.0:</strong> The image became fully backwards compatible with the older <code>doitandbedone/ispyagentdvr</code> image; no directory mapping changes are needed when switching, except in unRAID/Synology and other GUI-based container managers, where the documented mappings must be applied</li>
</ul>

<h2>Issues & Requests</h2>
<p>For issues or requests specific to this Docker image, use the image's GitHub repository: <a href="https://www.github.com/ispysoftware/agentdvr-docker" rel="nofollow noopener">https://www.github.com/ispysoftware/agentdvr-docker</a>
</p>
<p>For Agent DVR issues and requests, visit: <a href="https://www.reddit.com/r/ispyconnect/" rel="nofollow noopener">https://www.reddit.com/r/ispyconnect/</a>
</p>
<p>For details of the custom base image this container builds on, see: <a href="https://github.com/ispysoftware/ispyagentdvr-base-image" rel="nofollow noopener">https://github.com/ispysoftware/ispyagentdvr-base-image</a>
</p>
