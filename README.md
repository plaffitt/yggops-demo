# yggops-demo

After successfully installing the YggOps service, you can apply the example configuration file and look at the logs to see the service running.

```shell
# copy the example configuration file to the correct location
cp ./demo-config.yaml /etc/yggops/config.yaml

# copy the env file used in the docker-compose plugin in the defined location
cp ./gitea.env /etc/yggops/

# restart the service and follow the logs
systemctl restart yggops
journalctl -u yggops -f
```

Once the reconciliation done, you should be able to access your gitea instance at `http://<server_url>:3000`. If you type `docker ps`, you will also see gitea containers running.
