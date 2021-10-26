### For mysql-exporter

```
CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'XXXXXXXX';
GRANT PROCESS, SUPER, REPLICATION CLIENT ON *.* TO 'exporter'@'localhost';
GRANT SELECT, PROCESS, SUPER, REPLICATION CLIENT ON performance_schema.* TO 'exporter'@'localhost';
```