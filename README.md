# DockerSqlCompare

### Delete all containers
docker rm $(docker ps -a -q)

### Delete all images 
docker rmi $(docker images -q)

docker rmi $(docker images --filter "dangling=true")

