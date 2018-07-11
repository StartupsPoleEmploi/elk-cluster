# Dependencies

You will need Docker and docker-compose:

- [Docker install](https://docs.docker.com/engine/installation/)
- [docker-compose install](https://docs.docker.com/compose/install/)

# Quickstart

Run all services:

  make up

Configure Kibana (TODO)

Configure filebeat on the ngixn server (TODO)

# Operations

Obtain stats on docker container resource usage:

  docker stats

Tail logs from a specific container:
  
  docker-compose logs --tail=0 -f containername

# Troubleshooting

## `max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]`

[Elasticsearch uses mmapfs to store shard index](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html) and thus requires a higher value for `map_map_count`. Add `vm.max_map_count = 262144` to `/etc/sysctl.conf` on the host, then reload sysctl:

  sudo sysctl --system
