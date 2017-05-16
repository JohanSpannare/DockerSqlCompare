# DockerSqlCompare

### Delete all containers
docker rm $(docker ps -a -q)
### Delete all containers not running
docker rm $(docker ps -q --filter "status=exited")

### Delete all images 
docker rmi $(docker images -q)
### Delete all images dangling
docker rmi $(docker images --filter "dangling=true")



