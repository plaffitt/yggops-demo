# YggOps Quickstart Template 🚀

Welcome to the YggOps Quickstart Template! Its goal is to quickly help you configure your first YggOps instance and deploy a simple service using it. It is a GitHub template repository, so you can use it as a starting point for your own projects.

Before starting, ensure that you have the following installed:

- Docker: <https://docs.docker.com/engine/install/>
- YggOps: <https://github.com/plaffitt/yggops#installation>

Ready? Good, let's get started!

## Deploying a simple web server 👷

First, create a new repository using this template and clone it to your local machine.

Edit the `config.yaml` so it uses the private key that you added to your GitHub account during installation. Set a port if you like, the default is `:3000`. In the repository field of the `hello-world` project, replace `YOUR_NAME/YOUR_REPO_NAME` with your GitHub username and the name of the repository you created from this template. Commit and push.

If the host where you installed YggOps is a remote server, clone your repository and `cd` into it, if you're running it locally you already have everything you need.

You can now apply the configuration by running the following commands:

```shell
cp ./config.yaml /etc/yggops/config.yaml
cp ./*.env /etc/yggops/ # environment variables for the two docker compose stacks
systemctl restart yggops
```

You can then check that the service is running and follow its logs using systemd commands (`systemctl status yggops` and `journalctl -u yggops -f`).

Once the reconciliation done, you should be able to access your web server at `http://<server_url>:8080`, and if you type `docker ps`, you will see your container running.

Congratulation! You've deployed your first project using YggOps 🎉

## Configuring a webhook 🪝

If you try to edit `hello-world/index.html`, you will see that you have to wait for the reconciliation to be done to see the changes. Let's add a webhook to automate this process!

If you take a closer look at the `config.yaml`, you will see that a webhook is already defined for the project `hello-world`, so you just have to configure your GitHub repository to trigger it with the right secret (that you should change by the way). You can find the endpoint of the webhook in the startup logs of YggOps, it should look like `http://<ip>:<port>/webhooks/<provider>/<project>`. You must set the content type to `application/json`, and since we didn't use a reverse-proxy with auto-TLS like [caddy](https://caddyserver.com/docs/automatic-https) for instance, you have to **disable** SSL verification.

If you run YggOps locally, you should take a look at the [awesome-tunneling](https://github.com/anderspitman/awesome-tunneling) repository to expose your service to the internet.

Once it's done, you should be able to push and see the changes applied automatically to your service. 🚀

Alright! You're now ready to start your own project using YggOps! If you have any questions or bugs, feel free to open an issue on the [YggOps issue tracker](https://github.com/plaffitt/yggops/issues/new).
