# Supervisor-Dashboard

Step 1. Deploy the `vmsvc-influxdb.yaml` in the Supervisor Namespace. 

```
kubectl apply -f vmsvc-influxdb.yaml -n demo1
```

Step 2. Changes to be made to the Supervisor Telegraf Configmap. Login to the Supervisor Control Plane VM and modify the CM.

```
kubectl edit cm -n vmware-system-monitoring telegraf-config
```

```
    [[outputs.influxdb_v2]]
       urls = ["https://vmware-influxdb.demo1.svc.cluster.local"]
       organization = "VMware"
       token = "{{INFLUXDB API TOKEN}}"
       bucket = "Supervisor"
       insecure_skip_verify = true
```

Restart the Telegraf Daemonset.
```
kubectl rollout restart  -n vmware-system-monitoring daemonset telegraf
```

Step 3. Validate data is flowing to InfluxDB.

Step 4. Setup Grafana instance and enjoy the dashboards. 

```
kubectl apply -f grafana.yaml -n demo1
kubectl apply -f grafana-dashboard-1.yaml -n demo1
kubectl apply -f grafana-dashboard-2.yaml -n demo1
```

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



