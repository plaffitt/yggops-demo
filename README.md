# yggops-demo

```bash
sudo -i

# after running this command, don't forget to add the public key to your github/gitlab account
ssh-keygen -t ed25519

git clone https://github.com/plaffitt/yggops.git
cd yggops

make build install

# you can make sure that the service is running by running the following command
journalctl -u yggops -f

cat /etc/yggops/config.yaml
curl https://raw.githubusercontent.com/plaffitt/yggops-demo/refs/heads/main/yggops.yaml > /etc/yggops/config.yaml
systemctl restart yggops
```
