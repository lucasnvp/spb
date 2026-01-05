# How to debug Spark Jobs

## How to connect to the cluster

[Start point](https://adroll.atlassian.net/wiki/spaces/SRE/pages/2667544679/Plan+B+access+without+Banyan)

```shell
sshuttle \
  --ssh-cmd 'ssh -q -o TCPKeepAlive=yes -o ServerAliveInterval=120 -o CheckHostIP=no -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null' \
  --dns \
  --python python3 \
  --remote ec2-user@ssh-proxy.internal.adroll.com \
  10.0.0.0/8 \
  172.0.0.0/8 \
  192.168.0.0/16
```
