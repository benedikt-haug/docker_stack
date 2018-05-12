# docker_stack
This module contains my docker stack yaml files. All of them should run in docker swarm mode.

You can use this ugly piece of code in your crontab to automate updates for all stacks:
``` export $(cat ~/docker_stack/.env); docker images |grep -v REPOSITORY|awk '{print $1}' | sort | uniq |xargs -L1 docker pull && for i in nextcloud nginx-proxy postgres ttrss teamspeak; do docker stack deploy -c ~/docker_stack/$i.yaml $i; done```
