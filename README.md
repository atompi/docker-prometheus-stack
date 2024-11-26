## Installation

```
sudo rm -rf data
mkdir -p data/{grafana/data,grafana/log,grafana/provisioning,victoriametrics/vmstorage1,victoriametrics/vmstorage2,victoriametrics/vmstorage3,victoriametrics/vmagent}

mkdir -p resources/grafana/data/plugins/
curl -L https://github.com/VictoriaMetrics/victoriametrics-datasource/releases/download/v0.10.3/victoriametrics-datasource-v0.10.3.tar.gz -o resources/grafana/data/plugins/vm-plugin.tar.gz

docker compose up -d

tar -zxf resources/grafana/data/plugins/vm-plugin.tar.gz -C data/grafana/data/plugins/
cp resources/grafana/provisioning/datasources/vm-cluster.yaml data/grafana/provisioning/datasources/
cp resources/grafana/provisioning/dashboards/dashboards.yaml data/grafana/provisioning/dashboards/
cp -r resources/grafana/data/dashboards data/grafana/data/

docker compose restart grafana
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
