# Deploy

Check that you have cloned [signoz/signoz](https://github.com/signoz/signoz)
and currently are in `signoz/deploy` folder.

## Docker

If you don't have docker set up, please follow [this guide](https://docs.docker.com/engine/install/)
to set up docker before proceeding with the next steps.

### Using Install Script

Now run the following command to install:

```sh
./install.sh
```

### Using Docker Compose

If you don't have docker compose set up, please follow [this guide](https://docs.docker.com/compose/install/)
to set up docker compose before proceeding with the next steps.

```sh
cd deploy/docker
docker compose up -d
```

Open http://localhost:8080 in your favourite browser.

To start collecting logs and metrics from your infrastructure, run the following command:

```sh
cd generator/infra
docker compose up -d
```

To start generating sample traces, run the following command:

```sh
cd generator/hotrod
docker compose up -d
```

In a couple of minutes, you should see the data generated from hotrod in SigNoz UI.

For more details, please refer to the [SigNoz documentation](https://signoz.io/docs/install/docker/).
