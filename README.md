# README

## Configure WSL for Elasticsearch

WLS configuration needs to be updated to ensure Elasticsearch runs without issues.

Your `%userprofile%\.wslconfig` file needs to container the follow:
```
[wsl2]
kernelCommandLine = sysctl.vm.max_map_count=262144
```
It's also a good idea to ensure the memory and CPU limits for WSL is set to an adequate level, e.g.:
```
[wsl2]
memory=50GB # Limits VM memory in WSL 2 to 4 GB
processors=10 # Makes the WSL 2 VM use two virtual processors
```

## Configure APM in Kibana:

In order for Elasticsearch to receive telemetry data, the APM integration needs to be updated once all the services have started:

* Navigate to: http://localhost:5601/app/apm/services
* Log in with
  * user: elastic
  * password: change_me
* Click `Add the APM Integration`
* Click `Add Elastic APM`
* Click `Save and continue`
* Click `Add Elastic Agent later`
* Navigate to: http://localhost:5601/app/apm/services

This only needs to be done when starting the services the first time.   Subsequent startup will load the Elastisearch configuration that was persisted in `./es_data`