
mvn spring-boot:build-image -Dmodule.image.name=sflight

mvn spring-boot:build-image -Dmodule.image.name=sflight-native -Pnative

cds bind sflight-db -2 sflight-db
cds bind sflight-uaa -2 sflight-uaa

cds bind --exec -- sh -c 'docker run --rm -p 8080:8080 -e VCAP_SERVICES="$VCAP_SERVICES" -e "SPRING_PROFILES_ACTIVE=cloud" sflight-native:latest'


SPRING_PROFILES_ACTIVE=cloud cds bind --exec -- mvn clean package -Pnative
