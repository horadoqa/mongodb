# mongodb

## Instalação

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -

apt-key list

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

sudo apt-get update

sudo apt-get install -y mongodb-org

```

## Serviço

```bash
sudo systemctl status mongod
sudo systemctl start mongod
sudo systemctl restart mongod
sudo systemctl stop mongod
```

## Verifique os Logs do MongoDB

```bash
/var/log/mongodb/mongod.log
```

Use o comando a seguir para ver as últimas entradas dos logs:

```bash
tail -n 50 /var/log/mongodb/mongod.log
```

## Verifique a Configuração do MongoDB

Certifique-se de que a configuração do MongoDB não está restringindo as conexões. O arquivo de configuração normalmente está localizado em:

```bash
/etc/mongod.conf
```

## Verifique a seção net e certifique-se de que a configuração bindIp está correta:

net:
  bindIp: 127.0.0.1
  port: 27017


## Firewall
Verifique se há algum firewall bloqueando a porta 27017. Você pode usar o ufw (se estiver disponível) para permitir o tráfego nessa porta:

```bash
sudo ufw allow 27017
```
