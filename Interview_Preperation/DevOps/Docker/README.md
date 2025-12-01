Beginner (Basics)
1. What is Docker?

A platform to build, ship, and run applications inside lightweight containers.

2. What is a container?

A lightweight, isolated runtime environment using OS-level virtualization.

3. What is an image?

A read-only template used to create containers.

4. Difference between container and VM?
Container	VM
Shares host kernel	Has separate OS
Lightweight	Heavy
Starts in seconds	Slow startup
Less resource usage	High resource usage
5. What is Dockerfile?

A text file with instructions to build a Docker image.

Intermediate
6. What does the COPY vs ADD instruction do?

COPY → copies local files

ADD → same + supports URL and tar extraction

7. What is Docker Compose?

Tool for running multi-container apps defined via docker-compose.yml.

8. What is a Docker volume?

Persistent storage mechanism independent of container lifecycle.

9. What are the common Docker commands?

docker build

docker run

docker ps

docker logs

docker exec

10. What is Docker Hub?

Public registry for storing/pulling images.

Advanced
11. What is multi-stage Docker build?

Technique to optimize image size by using multiple FROM stages.

12. How do you reduce Docker image size?

Use small base images (alpine)

Multi-stage builds

Clean unused packages

.dockerignore

13. Explain Docker networking types.

Bridge (default)

Host (uses host network)

Overlay (for Swarm / multi-host)

None

14. How do you debug a running container?

docker exec -it <container> sh

15. What is a Docker registry?

Storage for Docker images (ECR, Docker Hub, Harbor).

16. What is the difference between ENTRYPOINT and CMD?

ENTRYPOINT → always executed

CMD → default arguments for ENTRYPOINT

17. How to pass environment variables in Docker?

docker run -e VAR=value

18. Explain the Docker layered architecture.

Images consist of layers; writable layer is added when running container.

19. What is the use of .dockerignore?

Excludes unnecessary files from build context.

20. How do you secure Docker containers?

Use non-root users

Scan images

Limit resources

Sign images

Use trusted base images

Scenario-Based
21. A container keeps restarting—how do you troubleshoot?

Check logs → docker logs

Check exit code

Check healthcheck

Validate entrypoint/cmd

22. Your Docker build is slow — how do you optimize?

Reorder Dockerfile instructions

Leverage build cache

Use smaller base images

23. How do you share data across containers?

Volumes or bind mounts.

24. How to run a container in the background?

docker run -d

25. How do you connect two containers?

Using Docker networks or docker-compose.
