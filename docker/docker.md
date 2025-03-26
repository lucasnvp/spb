# Docker

[!CAUTION]

`Error response from daemon: Ports are not available: exposing port TCP 127.0.0.1:80 -> 0.0.0.0:0: failed to connect to /var/run/com.docker.vmnetd.sock: is vmnetd running?: dial unix /var/run/com.docker.vmnetd.sock: connect: no such file or directory`

```bash
sudo /Applications/Docker.app/Contents/MacOS/install remove-vmnetd
sudo /Applications/Docker.app/Contents/MacOS/install vmnetd
```

