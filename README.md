
# OKD Monitoring Stack

This project deploys a full infrastructure monitoring stack on OpenShift (OKD), using Prometheus Operator, Grafana, and Node Exporter.

## 🎯 Objective

To monitor cluster resource usage such as:
- CPU & Memory (node-level)
- PVC storage usage
- Pod resource usage

## 🧰 Tools Used

- OpenShift (OKD 4.x)
- Prometheus Operator
- Grafana
- Node Exporter

## 🛠️ Deployment Steps

### 1. Deploy Prometheus Operator
```bash
oc apply -f prometheus/prometheus-operator.yaml
```

### 2. Create Prometheus Instance
```bash
oc apply -f prometheus/prometheus-instance.yaml
oc apply -f prometheus/prometheus-service.yaml
```

### 3. Deploy Node Exporter
```bash
oc apply -f node-exporter/deployment.yaml
oc apply -f node-exporter/service.yaml
```

### 4. Deploy Grafana
```bash
oc apply -f grafana/grafana-deployment.yaml
oc apply -f grafana/grafana-service.yaml
```

### 5. Configure Grafana Data Source
```bash
oc apply -f grafana/grafana-datasource.yaml
```

## 📊 Dashboards

To import dashboards:
- Go to Grafana UI → Dashboards → Import
- Upload JSON files from `grafana/dashboards/`

## 🔄 Future Enhancements
- Alerting via Alertmanager
- Integration with Slack/email
- Add HPA monitoring
- Monitor custom applications

## 📚 References
- https://github.com/prometheus-operator
- https://grafana.com/grafana/dashboards
- https://docs.openshift.com/container-platform/4.12/monitoring
