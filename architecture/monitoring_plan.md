# Simple Monitoring Plan

## 1. What We Monitor
- Data drift (changes in incoming data)
- Model performance (MCC, recall for fraud cases)
- System health (API uptime, errors, CPU/RAM)

## 2. Tools Used
- Prometheus → collects metrics
- Grafana → shows dashboards
- Evidently or NannyML → detects drift

## 3. Why Monitoring Is Needed
- To check if the model is still accurate
- To detect data changes early
- To ensure the API is running smoothly

## 4. Next Steps
1. Add Prometheus metrics to the model API
2. Connect Prometheus to Grafana
3. Create simple dashboards (latency, MCC, drift)
4. Add drift reports using Evidently/NannyML

