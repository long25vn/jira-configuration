# Cấu hình Jira

## Khởi động bằng docker

```
docker volume create --name jiraVolume
docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira" -d -p 8080:8080 atlassian/jira-software
```

## Tạo container Postgres 
```
docker run --name postgres -e POSTGRES_PASSWORD=123456 -d -p 5432:5432 postgres:alpine
```

#### Truy cập container Postgres, tạo database kết nối Jira

```
docker exec -it postgres /bin/sh
```

```
// Tạo database
CREATE DATABASE jiradb WITH ENCODING 'UNICODE' LC_COLLATE 'C' LC_CTYPE 'C' TEMPLATE template0;
```

```
// gán quyền truy cập database
// GRANT ALL PRIVILEGES ON DATABASE <Database Name> TO <Role Name>
GRANT ALL PRIVILEGES ON DATABASE jiradb TO 
```
