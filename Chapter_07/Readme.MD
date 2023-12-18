How to List Containers in Docker? 
How to Start Stop Remove Containers? 
How to Remove All Containers not Running in Docker?

Commands for listing containers, starting/stopping/removing containers, and removing all containers that are not running in Docker:

### List Containers:

To list all running containers:

```bash
docker ps
```

To list all containers (including stopped ones):

```bash
docker ps -a
```

### Start, Stop, Remove Containers:

#### Start a Container:

```bash
docker start <container_id_or_name>
```

#### Stop a Container:

```bash
docker stop <container_id_or_name>
```

#### Remove a Container:

To remove a stopped container:

```bash
docker rm <container_id_or_name>
```

To forcefully remove a running container, you can use the `-f` flag:

```bash
docker rm -f <container_id_or_name>
```

### Remove All Containers not Running:

To remove all stopped containers:

```bash
docker container prune
```

This command will prompt you to confirm the removal of all stopped containers.

If you want to remove all containers (both running and stopped) without confirmation, you can use the `-f` flag:

```bash
docker container prune -f
```

Be cautious when using the `-f` flag, as it removes all containers without confirmation.

These commands cover basic container management tasks in Docker. Feel free to adapt them to your specific use case and requirements.
