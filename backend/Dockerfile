# Image de base : Java 17 (JRE suffit pour exécuter, pas besoin du JDK)
FROM eclipse-temurin:17-jre

# Dossier de travail dans le conteneur
WORKDIR /app

# Copie du JAR produit par "mvn package" (stage Package du pipeline)
COPY target/*.jar app.jar

# Port d'écoute de Spring Boot dans le conteneur
EXPOSE 8080

# Commande de démarrage
ENTRYPOINT ["java", "-jar", "app.jar"]
