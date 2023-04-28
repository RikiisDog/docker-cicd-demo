# Base Stage
FROM gradle:7 AS base
CMD ["bash"]

# Build Stage
FROM base AS test-and-build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# Production Stage
FROM openjdk:17 AS prod
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]