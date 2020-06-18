# apache dubbo admin

> You can run a container like this:
```
docker run -it \
-e registry.address=zookeeper://192.168.10.168:2181 \
-e config-center=zookeeper://192.168.10.168:2181 \
-e metadata-report.address=zookeeper://192.168.10.168:2181 \
-e root.user.name=root \
-e root.user.password=password \
-p 8080:8080 --name dubbo-admin yakun0622/dubbo-admin:0.2.0
```


| name                    |              default value |
| :---------------------- | -------------------------: |
| config-center           | zookeeper://127.0.0.1:2181 |
| registry.address        | zookeeper://127.0.0.1:2181 |
| metadata-report.address | zookeeper://127.0.0.1:2181 |
| root.user.name          |                       root |
| root.user.password      |                       root |


Finally, open url  `http://localhost:8080` in browser and use root/root to login


### Screenshot
![index](https://raw.githubusercontent.com/yakun0622/docker-files/master/dubbo-admin/images/dubbo-admin.png)
