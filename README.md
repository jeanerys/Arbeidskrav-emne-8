# Arbeidskrav-emne-8
Arbeidskrav emne 8

# Beskrivelse:
Et RESTful API for å administrere TODO-lister med ASP.NET Core og MySQL som database. Skal gjøre det lettere å kunne legge til, oppdatere, hente og slette oppgaver. 

# Viktige filer:
1. docker-compose.yml: definasjon av Nginx, REST API og MySQL sammarbeid med hverandre i Docker.
   - backend tjenesten kjører, bygger API'et (som har .NET Framework) og eksporterer port 5001 til vertsmaskinen.
   - db som er MySQL database konfigurert med passord.
   - nginx eksporterer port 80 til vertsmaskinen og sender trafikk tilbake til backend tjenesten.
   - backend-network som gjør at alle tjenestene kommuniserer på samme nettverk.
   - helsekontroll i db som sørger for at MySQL er tilgjengelig før de andre starter.
2. dockerfile: bestemmer hvordan REST API'et skal bygges, der den har ASP.NET bilde som base, bygger og kopierer til en ny docker container.
3. nginx setter opp en proxy for backend (REST API'et), håndterer HTTP forespørsler og sender tilbake via proxy_pass. Den håndterer også Swagger endepunktene i API'et.

# Docker Container
todoapi som inneholder tre docker containere:
1. todoapi-nginx-1: nginx container som fungerer som reverse proxy.
2. todoapi-backend-1: REST API container som kjører API'et.
3. todoapi-db-1: MySQL database som API'et bruker til lagring av data.

# Installasjon:
docker-compose up -d
docker ps
docker-compose down

# Docker Hub Images
docker pull jeadyb92/todo-api
docker pull jeadyb92/mysql-image
docker pull jeadyb92/nginx-image
