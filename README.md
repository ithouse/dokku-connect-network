# dokku-connect-network

Attach docker's network defined in the the host's `/home/dokku/<APP>/DOKKU_CONNECT_NETWORK` file after the app is deployed.

## requirements

- dokku 0.4.0+
- docker 1.6.x

## installation

```shell
# on 0.4.x
dokku plugin:install https://github.com/ithouse/dokku-connect-network.git  connect-network
```

## usage

To use, create a `DOKKU_CONNECT_NETWORK` file in `/home/dokku/<APP>`. For instance, if we have an application called `lolipop`:

```shell
touch /home/dokku/lolipop/DOKKU_CONNECT_NETWORK
chown dokku:dokku /home/dokku/lolipop/DOKKU_CONNECT_NETWORK
echo -n "rednet" > /home/dokku/lolipop/DOKKU_CONNECT_NETWORK
```

Next, Create the network that you would like to attach to your containers.:

```shell
docker network create rednet
```


Once that is done, any deploy should automatically attach network to your containers.

