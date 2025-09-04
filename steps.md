```
// sonarqube practice 

0. Install Sonar Scanner 

// sonar scanner 
https://docs.sonarsource.com/sonarqube-server/9.7/analyzing-source-code/scanners/sonarscanner/

choco install sonarqube-scanner.portable -y
winget install SonarSource.SonarScanner
setx PATH "$env:PATH;C:\sonar-scanner\bin" /M
$env:PATH += ";C:\sonar-scanner\bin"

sonar-scanner -v

1. use docker compose file from cloning repo 

git clone https://github.com/atulkamble/basic-SonarQube-project.git

cd basic-SonarQube-project

2. run sonar scanner containers

docker-compose up -d 

docker container ls

3. from browser >> login 

http://localhost:9000 

add username, password >> admin, admin 

change password >> Admin@123456

4. create local project 

project name and code - cloudnautic 

5. create token >> profile >> 

copy token and paste sonar-project.properties

6. cli >> sonar-scanner

7. sonar >> portal 
// crosscheck details 










```
