FROM maven:3.5-jdk-8-alpine AS build                                                                                                                                                          
                                                                                                                                                                                              
RUN mkdir -p /root/dev/worker/                                                                                                               
                                                                                                                                                                                              
WORKDIR /root/dev/worker/                                                                                                                                                                     
                                                                                                                                                                                              
COPY pom.xml pom.xml                                                                                                                                                                          
                                                                                                                                                                                              
RUN mvn dependency:resolve                                                                                                                                                                    
                                                                                                                                                                                              
COPY . .                                                                                                                                                                                      
                                                                                                                                                                                              
RUN mvn package                                                                                                                                                                               
                                                                                                                                                                                              
FROM openjdk:8-jre-alpine

EXPOSE 80
                                                                                                                                                                                              
WORKDIR /root/dev/worker/                                                                                                                                                                     
                                                                                                                                                                                              
COPY --from=build /root/dev/worker/target/worker-jar-with-dependencies.jar .                                                                                                                  
                                                                                                                                                                                              
CMD [ "java", "-jar", "worker-jar-with-dependencies.jar" ]