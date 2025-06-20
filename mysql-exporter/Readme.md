# Mysql Exporter

Create **exporter** user in MySQL:
```
CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'exporterpassword' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'localhost';
FLUSH PRIVILEGES;
```

Test by running the following command:
```
curl http://localhost:9104/metrics
```