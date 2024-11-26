```
sudo rm -rf data
mkdir -p data/{grafana/data,grafana/log,grafana/provisioning,victoriametrics/vmstorage1,victoriametrics/vmstorage2,victoriametrics/vmstorage3,victoriametrics/vmagent}

mkdir -p resources/grafana/plugins/
curl -L https://github.com/VictoriaMetrics/victoriametrics-datasource/releases/download/v0.10.3/victoriametrics-datasource-v0.10.3.tar.gz -o resources/grafana/plugins/vm-plugin.tar.gz
tar -zxf resources/grafana/plugins/vm-plugin.tar.gz -C data/grafana/data/plugins/
cp resources/grafana/datasources/vm-cluster.yaml data/grafana/provisioning/datasources/
cp -r resources/grafana/dashboards/* data/grafana/provisioning/dashboards/

docker compose up -d
```

## Data source

- Default

```
vm-cluster
```

- Prometheus

```
http://vmselect:8481/select/0/prometheus
```
