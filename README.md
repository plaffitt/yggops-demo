# yggops-demo

```bash
sudo apt install make
sudo usermod -aG docker

ssh ubuntu@185.145.250.212
sudo -i

ssh-keygen -t ed25519

git clone https://github.com/plaffitt/yggops.git
cd yggops

touch yggops && make install
make docker-build install
journalctl -u yggops -f

cat /etc/yggops/config.yaml
git@github.com:plaffitt/yggops-demo.git
curl https://raw.githubusercontent.com/plaffitt/yggops-demo/refs/heads/main/yggops.yaml > /etc/yggops/config.yaml
systemctl restart yggops
```
