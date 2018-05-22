# DockerSqlCompare

### Delete all containers
docker rm $(docker ps -a -q)
### Delete all containers not running
docker rm $(docker ps -q --filter "status=exited")

### Delete all images 
docker rmi $(docker images -q)
### Delete all images dangling
docker rmi $(docker images -q --filter "dangling=true")

### Rebalancing containers accross all nodes in collection
docker service ls --format "{{.Name}}" | %{$serviceId = $_; docker service ps $_ -f desired-state=running --format "{{.Node}}" | Group | %{if($_.Count -gt 1){Write "Rebalancing $serviceId due to dupplicate containers on same node $_";docker service update $serviceId --force --detach=true }} }




