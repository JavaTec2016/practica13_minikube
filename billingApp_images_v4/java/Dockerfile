FROM eclipse-temurin:17-jdk-alpine
RUN addgroup -S devopsc && adduser -S -G devopsc javams 
USER javams:devopsc
ENV JAVA_OPTS=""
ARG JAR_FILE=billing-0.0.4-SNAPSHOT.jar
COPY ${JAR_FILE} /app.jar
# si se copia como un directorio tira error, debe ser el puro jar
RUN test -f /app.jar || (echo "ERROR: /app.jar is not a file" && ls -la /app.jar && exit 1)
 # use a volume is mor efficient and speed that filesystem
VOLUME /tmp
EXPOSE 7080
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]

