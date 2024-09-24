# mongodb

## Instalação

Importar a chave pública:

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb.gpg

apt-key list
```

## Adicionar o repositório:

```bash
echo "deb [signed-by=/usr/share/keyrings/mongodb.gpg] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```
## Atualizar os repositórios:

```bash
sudo apt-get update
```

## Instalar o MongoDB:

```bash
sudo apt-get install -y mongodb-org
```

## Serviço

Verificando Status

```bash
sudo systemctl status mongod

○ mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: https://docs.mongodb.org/manual
```

Startando o serviço

```bash
sudo systemctl start mongod
```

Verificando Status

```bash
sudo systemctl status mongod
● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-09-24 07:47:10 -03; 11s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 286387 (mongod)
     Memory: 72.3M
     CGroup: /system.slice/mongod.service
             └─286387 /usr/bin/mongod --config /etc/mongod.conf

Sep 24 07:47:10 DESKTOP-059018K systemd[1]: Started MongoDB Database Server.
Sep 24 07:47:10 DESKTOP-059018K mongod[286387]: {"t":{"$date":"2024-09-24T10:47:10.507Z"},"s":"I",  "c":"CONTROL",  "id>
lines 1-11/11 (END)
```

## Restart e stop

```bash
sudo systemctl restart mongod
sudo systemctl stop mongod
```

## Verifique os Logs do MongoDB

```bash
cat /var/log/mongodb/mongod.log
```

Use o comando a seguir para ver as últimas entradas dos logs:

```bash
tail -n 50 /var/log/mongodb/mongod.log
```

## Verifique a Configuração do MongoDB

Certifique-se de que a configuração do MongoDB não está restringindo as conexões. O arquivo de configuração normalmente está localizado em:

```bash
cat /etc/mongod.conf
```

## Verifique a seção net e certifique-se de que a configuração bindIp está correta:

    net:
    bindIp: 127.0.0.1
    port: 27017


## Firewall
Verifique se há algum firewall bloqueando a porta 27017. Você pode usar o ufw (se estiver disponível) para permitir o tráfego nessa porta:

```bash
sudo ufw allow 27017

Skipping adding existing rule
Skipping adding existing rule (v6)
```

## Removendo o repositório

```bash
sudo rm /etc/apt/sources.list.d/mongodb-org-*.list
```

## Via DOCKER

Instalar o Docker (se ainda não estiver instalado):

```bash
sudo apt update
sudo apt install -y docker.io
```

## Executar MongoDB no Docker:

Após instalar o Docker, você pode executar o MongoDB com o seguinte comando:

```bash
sudo docker run --name mongodb -d -p 27017:27017 -v mongodb-data:/data/db mongo
```

## Executando

```bash
mongosh

test> help
```

```bash
show databases
admin   40.00 KiB
config  60.00 KiB
local   40.00 KiB
```


```bash
mongod
```