
mvn spring-boot:build-image -Dmodule.image.name=sflight

mvn spring-boot:build-image -Dmodule.image.name=sflight-native -Pnative

cds bind --exec -- sh -c 'docker run --rm -p 8080:8080 -e VCAP_SERVICES="$VCAP_SERVICES" srv:1.0.0-SNAPSHOT'

