FROM eclipse-temurin:21-jdk
FROM eclipse-temurin:21-jdk

WORKDIR /app

# 1. Copy everything
COPY . .

# 2. Repair the script (The fix we found earlier)
RUN apt-get update && apt-get install -y dos2unix && \
    dos2unix gradlew && \
    chmod +x gradlew

# 3. Build with SSL verification disabled
# We pass the -D flags directly to the JVM to tell it not to be picky about certs
CMD ["/bin/bash", "./gradlew", "build", "--no-daemon", "-Dbuild.gradle.skip.ssl=true", "-Djdk.tls.client.protocols=TLSv1.2"]