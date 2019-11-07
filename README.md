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
// Truy cập container
docker exec -it postgres /bin/sh
su postgres
psql
```

```
// Tạo database
CREATE DATABASE jiradb WITH ENCODING 'UNICODE' LC_COLLATE 'C' LC_CTYPE 'C' TEMPLATE template0;
```

####  Gán quyền truy cập database
```
// GRANT ALL PRIVILEGES ON DATABASE <Database Name> TO <Role Name>
GRANT ALL PRIVILEGES ON DATABASE jiradb TO 
```

### Truy cập `localhost:8080`
![](https://i.imgur.com/0e1lgKv.png)

### Trang cấu hình

<p align="center">
  <img width="750" src="https://i.imgur.com/wSQ3B5Q.png">
</p>


# Error

## Error1
<p align="center">
  <img width="500" src="https://i.imgur.com/cz4n1Qu.png">
</p>

### Nguyên nhân
> Một số chỉ sổ cấu hình lỗi

### Khắc phục 
```
docker exec -it container_jira /bin/sh
rm -rf JIRA_HOME/caches
```
exit container và khởi động lại container

## Error2

<p align="center">
  <img width="600" src="https://i.imgur.com/MeZTn79.png">
</p>

[https://community.atlassian.com/t5/Jira-articles/How-to-run-Jira-in-a-docker-container/ba-p/752697](https://community.atlassian.com/t5/Jira-articles/How-to-run-Jira-in-a-docker-container/ba-p/752697)


<p align="center">
  <img width="600" src="https://i.imgur.com/U3nHhRf.png">
</p>



# Tiếp theo
![](https://i.imgur.com/6tZUUwM.png)

![](https://i.imgur.com/aV45Mkd.png)

![](https://i.imgur.com/PQPh8di.png)

![](https://i.imgur.com/0p8kLMv.png)
