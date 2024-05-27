# Supervisor-Dashboard

## Dashboard 1 - CPU/Memory/Disk/Networking metrics. 

<img src="images/CPUimage1.png" title="CPU 1">
<img src="images/CPUimage2.png" title="CPU 2">
<img src="images/CPUimage3.png" title="CPU 3">
<img src="images/CPUimage4.png" title="CPU 4">

---

## Dashboard 2 - Kubernetes metrics. 

<img src="images/K8simage1.png" title="K8S 1">
<img src="images/K8simage2.png" title="K8S 2">
<img src="images/K8simage3.png" title="K8S 3">

---

Changes to be made to the Supervisor Telegraf Configmap

```
    [[outputs.influxdb_v2]]
       urls = ["https://vmware-influxdb.demo1.svc.cluster.local"]
       organization = "VMware"
       token = "{{INFLUXDB API TOKEN}}"
       bucket = "Supervisor"
       insecure_skip_verify = true
```

