# wekan-docker-compose

This project is based on [wekan](https://github.com/wekan/wekan/blob/master/docker-compose.yml).

It contains:
- wekan
- mongodb
- wekan-dingtalk-webhooks-proxy-server

## usage

After clone this project, we need init submodle:

```
git submodule update --init
```

And then make the config files for wekan-dingtalk-webhooks-proxy-server:

```
cd wekan-dingtalk-webhooks-proxy-server
cp -i config/config-server-example.json config/config-server.json
cp -i config/config-account-example.json config/config-account.json
```

After editing the configuration files, you may need also modify the `ROOT_URL` config in `docker-compose.yml`.

Now execute the following command to start the services:

```
docker-compose build
docker-compose up -d
```

Finally, setup a webhook in wekan, the webhook address should be: `http://wekan-dingtalk-webhooks-proxy-server:8080/api/wekan/webhook/`