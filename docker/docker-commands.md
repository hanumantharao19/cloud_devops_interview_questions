20. Containerization and Orchestration
Docker
 docker – Docker command-line interface (CLI) for managing
containers
o docker run <image> – Run a container from an image
o docker ps – List running containers
o docker ps -a – List all containers, including stopped ones
o docker build -t <image_name> . – Build an image
from a Dockerfile
o docker exec -it <container_id> bash – Start an
interactive bash shell inside a running container
o docker stop <container_id> – Stop a container
o docker rm <container_id> – Remove a container


o docker logs <container_id> – View logs of a container
o docker images – List available images
o docker rmi <image_name> – Remove an image
o docker network ls – List Docker networks
o docker-compose – Manage multi-container Docker
applications
 docker-compose up – Start up a multi-container
environment
 docker-compose down – Stop and remove containers
created by docker-compose
 docker-compose logs – View logs from containers
managed by docker-compose
