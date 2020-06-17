# apache dubbo admin

> You can run a container like this:
```
docker run -it \
-e REGISTRY_ADDRESS=zookeeper://192.168.10.168:2181 \
-e CONFIG_CENTER=zookeeper://192.168.10.168:2181 \
-e METADATA_REPORT_ADDRESS=zookeeper://192.168.10.168:2181 \
-p 8080:8080 dubbo-admin:0.2.0 dubbo-admin
```

- REGISTRY_ADDRESS: admin.registry.address
- CONFIG_CENTER: admin.config-center
- METADATA_REPORT_ADDRESS: metadata-report.address

Finally, open url `http://localhost:8080` in browser

### Screenshot
![index](https://raw.githubusercontent.com/apache/dubbo-admin/develop/doc/images/index.png)
