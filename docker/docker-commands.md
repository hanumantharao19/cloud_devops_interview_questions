20. Containerization and Orchestration
Docker
- docker – Docker command-line interface (CLI) for managing
containers
- docker run <image> – Run a container from an image
- docker ps – List running containers
- docker ps -a – List all containers, including stopped ones
- docker build -t <image_name> . – Build an image
from a Dockerfile
- docker exec -it <container_id> bash – Start an
interactive bash shell inside a running container
- docker stop <container_id> – Stop a container
- docker rm <container_id> – Remove a container


- docker logs <container_id> – View logs of a container
- docker images – List available images
- docker rmi <image_name> – Remove an image
- docker network ls – List Docker networks
- docker-compose – Manage multi-container Docker
applications
- docker-compose up – Start up a multi-container
environment
- docker-compose down – Stop and remove containers
created by docker-compose
- docker-compose logs – View logs from containers
managed by docker-compose
