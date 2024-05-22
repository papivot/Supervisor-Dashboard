# Supervisor-Dashboard

```
    [[outputs.influxdb_v2]]
       urls = ["https://vmware-influxdb.demo1.svc.cluster.local"]
       organization = "VMware"
       token = "{{INFLUXDB API TOKEN}}"
       bucket = "Supervisor"
       insecure_skip_verify = true
```