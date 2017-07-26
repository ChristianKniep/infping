# infping
Parse fping output, store result in influxdb 0.9

See blog post for more info https://hveem.no/visualizing-latency-variance-with-grafana


## Docker Setup

To get started, just fire up the `docker-compose.yml` as Docker Services on a local SWARM.

```
$ docker stack deploy --compose-file docker-compose.yml fping
Creating network fping_default
Creating service fping_backend
Creating service fping_frontend
$
```

You need to setup a retention policy `CREATE RETENTION POLICY "default" ON "fping" DURATION 30d REPLICATION 1 DEFAULT`.

After that build the tools and run it with the example configuration.


```bash
$ ./infping/infping google.de
  2017/07/26 13:15:34 Connected to influxdb! 4.99046ms, 1.2.4
  2017/07/26 13:15:34 Going to ping the following hosts: ["127.0.0.1" "8.8.8.8"]
```