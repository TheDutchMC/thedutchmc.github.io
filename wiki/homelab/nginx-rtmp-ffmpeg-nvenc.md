# NGINX with the RTMP module and transcoding with FFMPEG and NVENC
This guide will show you how to compile NGINX with the RTMP module, and how to set up FFMPEG to be able to use Nvidia NVENC.

### Preparations
1. If you are in an LXC, follow the beginnings of [this guide](/wiki/homelab/deskop-environment-in-container.md)
2. Make sure you have an NVIDIA drive installed.
3. ``sudo apt update``
4. ``sudo apt install build-essential git``
5. ``sudo apt install libpcre3-dev libssl-dev zlib1g-dev``

### Compiling NGINX
1. ``mkdir -p /opt/nginx``
2. ``cd /opt/nginx``
3. ``git clone https://github.com/arut/nginx-rtmp-module.git``
4. ``git clone https://github.com/nginx/nginx.git``
5. ``cd nginx``
6. ``./auto/configure --add-module=../nginx-rtmp-module``
7. ``make``
8. ``sudo make install``

We've now got a working NGINX installation. Next up we should add a service file so we can start and stop it easily.

9. Open ``/usr/local/nginx/conf/nginx.conf`` and add at the top: ``pid /run/nginx.pid;``
10. Open ``/etc/systemd/system/nginx.service`` and paste in:
```
[Unit]
Description=The NGINX HTTP and reverse proxy server with RTMP
After=syslog.target network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/local/nginx/sbin/nginx -t
ExecStart=/usr/local/nginx/sbin/nginx
ExecReload=/usr/local/nginx/sbin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```
11. ``sudo systemctl daemon-reload``
12. ``sudo systemctl start nginx``


> **Note:** You need at least driver version 455.28!

### CUDA
1. ``mkdir -p /opt/cuda``
2. ``cd /opt/cuda``
3. ``wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin``
4. ``sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600``
5. ``wget https://developer.download.nvidia.com/compute/cuda/11.1.1/local_installers/cuda-repo-ubuntu2004-11-1-local_11.1.1-455.32.00-1_amd64.deb``
6. ``sudo dpkg -i cuda-repo-ubuntu2004-11-1-local_11.1.1-455.32.00-1_amd64.deb``
7. ``sudo apt-key add /var/cuda-repo-ubuntu2004-11-1-local/7fa2af80.pub``
8. ``sudo apt-get update``
9. ``sudo apt-get -y install cuda``

> **Note:** If you are working in an LXC container you should verify that the driver version is still the same version as your host.

### FFMPEG
1. ``mkdir -p /opt/ffmpeg/``
2. ``cd /opt/ffmpeg``
3. ``git clone https://git.ffmpeg.org/ffmpeg.git``
4. ``git clone https://github.com/FFmpeg/nv-codec-headers.git``
5. ``cd nv-codec-headers``
6. ``make install``
7. ``cd ../ffmpeg``
8. ``sudo apt install yasm libx64``
9. ``./configure --enable-cuda --enable-cuvid --enable-nvenc --enable-nonfree --enable-libnpp --enable-gpl --enable-libx264 --extra-cflags=-I/usr/local/cuda/include  --extra-ldflags=-L/usr/local/cuda/lib64``
10. ``make -j -s``

We've now got FFMPEG compiled with support for NVENC. We can now symlink it to ``/usr/bin`` so we can use the ``ffmpeg`` command anywhere on the system.
11. ``ln -s /opt/ffmpeg/ffmpeg/ffmpeg /usr/bin``
12. You should verify that ffmpeg works now.

### Configuration

