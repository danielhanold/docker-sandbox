### Launch Instructions
To bring up all three projects using one command, use this command:
```
docker-compose -f nginx-proxy/docker-compose.yml -f cms/docker-compose.yml -f cda/docker-compose.yml up -d
```
### Alias Setup
To execute docker-compose commands for all three projects, create an alias for the above command
and use it like a regular docker-compose command. Use "mydkenv" as an example, and export this
in your .bashrc file.
```
alias="docker-compose -f nginx-proxy/docker-compose.yml -f cms/docker-compose.yml -f cda/docker-compose.yml"
```
