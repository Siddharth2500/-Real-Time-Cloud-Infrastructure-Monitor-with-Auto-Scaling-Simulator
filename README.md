# 📡 Real-Time Cloud Infrastructure Monitor & Auto-Scaling Simulator
Python · Matplotlib · Pandas  

CloudPulse is a Python-based simulator that demonstrates **real-time cloud monitoring** with **auto-scaling logic**.  
It mimics services like AWS Auto Scaling, Azure VM Scale Sets, and GCP Instance Groups by:  

- Monitoring CPU, memory, and network metrics  
- Triggering scaling events based on thresholds  
- Generating alerts, dashboards, and reports  

Perfect for **learning cloud scaling strategies** and **DevOps monitoring fundamentals**.  

## 🛠 Tech & Languages
| Layer       | Tech           | Notes |
|-------------|---------------|-------|
| Language    | Python 3.10+   | Core project language |
| Data        | Pandas         | Metric collection & CSV export |
| Visualization | Matplotlib   | 4-panel monitoring dashboard |
| Simulation  | Custom Classes | CloudResource + AutoScaler |
| Platform    | Google Colab / Local | Works in both environments |

---

## 🌐 Architecture
**Flow**
1. Instances simulate CPU, memory, and network activity.  
2. Monitor collects metrics every 2 seconds.  
3. AutoScaler checks thresholds → scales up/down (min=2, max=10).  
4. Alerts log scaling events and anomalies.  
5. Reports + PNG dashboards are generated.  

**Diagram**
┌───────────────────────────┐
│ CloudInfrastructureMonitor │
│ - Collect metrics │
│ - Run scaling loop │
│ - Generate reports │
└───────────┬───────────────┘
│
┌────────▼─────────┐
│ AutoScaler │
│ - Threshold logic│
│ - Min/Max limits │
└────────┬─────────┘
│
┌────────▼─────────┐
│ CloudResource │
│ - CPU/Memory I/O │
│ - Simulated load │
└──────────────────┘

yaml
Copy code

---

## 📦 Repository Structure
cloudpulse/
├─ app/
│ ├─ monitor.py # Main orchestrator
│ ├─ autoscaler.py # Scaling logic
│ └─ resource.py # Simulated resources
├─ outputs/
│ ├─ cloud_metrics.csv
│ └─ cloud_metrics_dashboard.png
├─ tests/
│ └─ test_autoscaler.py
├─ requirements.txt
└─ README.md

yaml
Copy code

-----

## ▶️ Quick Start (Google Colab)
Open [Google Colab](https://colab.research.google.com), paste the project code, then run:

```python
monitor = CloudInfrastructureMonitor()
monitor.monitor_loop(duration=30, interval=2)
monitor.generate_report()
monitor.plot_metrics()
monitor.export_metrics_csv()
🔗 Key Features
📊 Real-Time Monitoring — CPU, memory, and network I/O every 2s

⚖️ Auto-Scaling Simulator — scale up >70% CPU, scale down <30%

🚨 Alerts — CPU >80%, memory >85%, scaling events logged

📑 Reports — min/max/avg + alert history

📈 Dashboards — 4 panels (CPU, Memory, Network, Instances)

📂 Data Export — CSV for Excel, Pandas, BI tools

📊 Output Examples
Dashboard (cloud_metrics_dashboard.png)

Panel 1: CPU usage with thresholds

Panel 2: Memory usage

Panel 3: Network throughput

Panel 4: Instance count (auto-scaling decisions)

CSV (cloud_metrics.csv)

Timestamp	Avg_CPU	Avg_Memory	Total_Network_IO	Instance_Count
14:30:15	45.23	62.18	1250.45	2
14:30:19	72.89	66.45	1450.23	3

🔧 Examples
Custom duration

python
Copy code
monitor.monitor_loop(duration=60, interval=1)
Custom scaling thresholds

python
Copy code
autoscaler = AutoScaler(
    min_instances=3,
    max_instances=15,
    scale_up_threshold=65,
    scale_down_threshold=35
)
monitor.autoscaler = autoscaler
Simulate traffic spike

python
Copy code
for resource in monitor.resources:
    resource.cpu_usage = 85
monitor.collect_metrics()
monitor.auto_scale()
🧪 Tests
Run with:

bash
Copy code
pytest -q
Covers:

Scaling up/down logic

Metric collection

Alerts triggering

🐳 Docker (Optional)
Build:

bash
Copy code
docker build -t cloudpulse:latest .
Run:

bash
Copy code
docker run cloudpulse:latest
☸️ Kubernetes (Future Work)
Wrap monitor in FastAPI/Flask REST API

Deploy as a container to Kubernetes

Expose /metrics for Prometheus scrapes

Use Horizontal Pod Autoscaler for demo

🔐 Production Notes
Integrate with AWS CloudWatch / Azure Monitor / GCP Monitoring

Store metrics in databases (Postgres, InfluxDB)

Send real alerts (Slack, Email)

Add anomaly detection with ML

👤 Author
Siddharth Raut — DevOps & Cloud Engineer

