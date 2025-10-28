# Wordpress with docker-compose

## Init wordpress
```
docker-compose up -d
```
Open http://your-ip:8080/wp-admin to set up your wordpress. (your-ip = localhost if you run it on your local machine)

Sau khi tạo xong tk admin và pass.
=> Cài nginx và DNS và https
=> Sửa file wp-config.php để trỏ về domain mới. Hoặc là vào mysql sửa ở table wp_options sửa siteurl và home thành domain mới.



docker exec -i mysql bash -lc \
  'mysqldump --user="3ddesigns" --password="Secret@123" \
   --databases "3ddesigns" --single-transaction --quick --routines --triggers --events --hex-blob' \
| gzip > backup/wp-db-$TS.sql.gz


docker exec -i mysql /opt/bitnami/mysql/bin/mysqldump \
  --user="3ddesigns" \
  --password="Secret@123" \
  --databases "3ddesigns" \
  --single-transaction --quick --routines --triggers --events --hex-blob \
  > backup/wp-db-$(date +%Y-%m-%d).sql