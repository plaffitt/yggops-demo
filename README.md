# yggops-demo

- install docker <https://docs.docker.com/engine/install/>
- install yggops
- setup webhook

Don't forget to edit the demo-config.yaml file to match your environment.

```shell

After successfully installing the YggOps service, you can apply the example configuration file and look at the logs to see the service running.

```shell
cp ./demo-config.yaml /etc/yggops/config.yaml
cp ./*.env /etc/yggops/
systemctl restart yggops
journalctl -u yggops -f
```

The `.env` files are used to set the environment variables for the two docker-compose stacks that we want to deploy.

Once the reconciliation done, you should be able to access your gitea instance at `http://<server_url>:3000`. If you type `docker ps`, you will also see gitea containers running.
