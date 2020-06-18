# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM maven:3-openjdk-8
RUN mkdir /source && wget https://github.com/apache/dubbo-admin/archive/0.2.0.zip && unzip -q 0.2.0.zip -d /source
WORKDIR /source/dubbo-admin-0.2.0
RUN sed -i 's/admin.registry.address=zookeeper\:\/\/127.0.0.1:2181/admin.registry.address=${registry.address\:zookeeper\:\/\/127.0.0.1:2181}/g' ./dubbo-admin-server/src/main/resources/application.properties
RUN sed -i 's/admin.config-center=zookeeper\:\/\/127.0.0.1:2181/admin.config-center=${config-center\:zookeeper\:\/\/127.0.0.1:2181}/g' ./dubbo-admin-server/src/main/resources/application.properties
RUN sed -i 's/admin.metadata-report.address=zookeeper\:\/\/127.0.0.1:2181/admin.metadata-report.address=${metadata-report.address\:zookeeper\:\/\/127.0.0.1:2181}/g' ./dubbo-admin-server/src/main/resources/application.properties
RUN sed -i 's/admin.root.user.name=root/admin.root.user.name=${root.user.name:root}/g' ./dubbo-admin-server/src/main/resources/application.properties
RUN sed -i 's/admin.root.user.password=root/admin.root.user.password=${root.user.password:root}/g' ./dubbo-admin-server/src/main/resources/application.properties

RUN mvn --batch-mode clean package -Dmaven.test.skip=true

FROM openjdk:8-jre
LABEL maintainer="dev@dubbo.apache.org"
COPY --from=0 /source/dubbo-admin-0.2.0/dubbo-admin-distribution/target/dubbo-admin-0.2.0.jar /app.jar
ENTRYPOINT ["java","-XX:+UnlockExperimentalVMOptions","-XX:+UseCGroupMemoryLimitForHeap","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
EXPOSE 8080
