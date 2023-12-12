# 使用 Docker 啟動 RabbitMQ 並啟用 SSL 功能

## 使用 OpenSSL 生成自簽名憑證和私鑰

首先建立 ssl 的目錄，被進入到 ssl 目錄內執行以下指令：

1. 生成私鑰 (key.pem)：

    ```shell
    openssl genpkey -algorithm RSA -out key.pem
    ```

2. 生成自簽名憑證 (cert.pem)：

    ```shell
    openssl req -new -key key.pem -out csr.pem
    openssl x509 -req -days 365 -in csr.pem -signkey key.pem -out cert.pem
    ```

## 啟動 RabbitMQ

憑證生成完畢回到上一層目錄，執行以下指令：

```shell
docker-compose up -d
```
