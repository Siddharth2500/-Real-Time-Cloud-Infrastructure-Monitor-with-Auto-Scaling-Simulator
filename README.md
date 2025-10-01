# Project 1: Real-Time Cloud Infrastructure Monitor with Auto-Scaling

## 📋 Table of Contents
- [Overview](#-overview)
- [Features](#-features)
- [Technical Architecture](#-technical-architecture)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration](#-configuration)
- [Output Files](#-output-files)
- [Customization](#-customization)
- [Learning Outcomes](#-learning-outcomes)
- [Real-World Applications](#-real-world-applications)
- [Troubleshooting](#-troubleshooting)
- [Production Deployment](#-production-deployment)
- [Related Technologies](#-related-technologies)
- [Performance Metrics](#-performance-metrics)
- [Interview Questions Covered](#-interview-questions-covered)
- [Enhancement Ideas](#-enhancement-ideas)
- [License](#-license)
- [Author](#-author)
- [Acknowledgments](#-acknowledgments)

---

## 🎯 Overview
This project simulates a **real-time cloud infrastructure monitoring system** with auto-scaling.  
It behaves like AWS Auto Scaling, Azure VM Scale Sets, or GCP Managed Instance Groups by:

- Monitoring CPU, memory, and network usage  
- Detecting anomalies  
- Automatically scaling resources up or down  

It’s designed to help you learn cloud management, auto-scaling, and DevOps monitoring strategies.

---

## 🌟 Features

### 1. Real-Time Monitoring
- Tracks CPU, memory, and network I/O  
- Updates every 2 seconds  
- Maintains 50-point history for trend analysis  

### 2. Intelligent Auto-Scaling
- **Scale Up**: CPU > 70%  
- **Scale Down**: CPU < 30%  
- Enforces min (2) and max (10) instance limits  
- Smart logic to avoid scaling thrashing  

### 3. Alert System
- CPU > 80% → Warning  
- Memory > 85% → Warning  
- Scaling event notifications with timestamps  

### 4. Reporting
- Infrastructure status dashboard  
- Max, min, and average statistics  
- Resource-level breakdown  
- Complete alert history  

### 5. Data Visualization
- 4-panel dashboard with:
  - CPU Usage  
  - Memory Usage  
  - Network I/O  
  - Instance Count  
- High-resolution PNG export (300 DPI)  

### 6. Data Export
- CSV export of all metrics  
- Timestamped entries for analysis  
- Compatible with Excel, Pandas, Power BI, Tableau  

---

## 🏗️ Technical Architecture

┌─────────────────────────────────────────┐
│ CloudInfrastructureMonitor (Main) │
│ - Orchestrates monitoring & scaling │
└─────────┬───────────────────────┬──────┘
│ │
┌──────▼───────┐ ┌──────▼──────┐
│ AutoScaler │ │ CloudResource│
│ - Thresholds │ │ - Metrics │
│ - Logic │ │ - Simulation │
└──────────────┘ └─────────────┘

yaml
Copy code

- **CloudResource**: Simulates metrics per instance  
- **AutoScaler**: Applies thresholds and scaling decisions  
- **CloudInfrastructureMonitor**: Main loop, alerts, reports  

---

## 💻 Installation

### Prerequisites
If using Google Colab:  
- `matplotlib` and `pandas` are already installed.  

If running locally:  
```bash
pip install matplotlib pandas
Run in Google Colab
Open Google Colab

Create a new notebook

Copy the project code into a cell and run

🚀 Usage
Basic Run
python
Copy code
monitor = CloudInfrastructureMonitor()
monitor.monitor_loop(duration=30, interval=2)
monitor.generate_report()
monitor.plot_metrics()
monitor.export_metrics_csv()
Custom Duration
python
Copy code
monitor.monitor_loop(duration=60, interval=1)
Custom Scaling
python
Copy code
autoscaler = AutoScaler(
    min_instances=3,
    max_instances=15,
    scale_up_threshold=65,
    scale_down_threshold=35
)
monitor.autoscaler = autoscaler
⚙️ Configuration
Monitoring Settings
Parameter	Default	Description
duration	30	Monitoring time (seconds)
interval	2	Metric collection frequency
maxlen	50	Number of history points

Auto-Scaling Settings
Parameter	Default	Description
min_instances	2	Minimum number of instances
max_instances	10	Maximum number of instances
scale_up_threshold	70	CPU% to trigger scale-up
scale_down_threshold	30	CPU% to trigger scale-down

Alert Thresholds
Metric	Threshold	Alert Level
CPU	80%	WARNING
Memory	85%	WARNING
Scaling	Any	INFO

📊 Output Files
cloud_metrics_dashboard.png

Panel 1: CPU usage (with thresholds)

Panel 2: Memory usage

Panel 3: Network I/O

Panel 4: Instance count

cloud_metrics.csv

Timestamp	Avg_CPU	Avg_Memory	Total_Network_IO	Instance_Count
14:30:15	45.23	62.18	1250.45	2

🎨 Customization
Cost optimization: calculate savings with/without scaling

Traffic spike simulation: force high CPU load

Multi-region deployment: add resources across regions

Resource types: mix EC2, Docker, Serverless, Azure VMs

🎓 Learning Outcomes
DevOps: IaC, monitoring, scaling, alerting

Cloud: elasticity, high availability, cost optimization

Python: OOP, real-time data handling, Pandas, Matplotlib

🌍 Real-World Applications
E-commerce: handle Black Friday traffic

Streaming: scale with viewers

APIs: adjust to request rate

Gaming: scale for player demand

Data pipelines: handle batch workloads

🐛 Troubleshooting
No graphs in Colab

python
Copy code
import matplotlib.pyplot as plt
%matplotlib inline
NameError: pd not defined → import pandas as pd

Too fast/slow → adjust interval

Low scaling activity → lower thresholds

Memory issues → reduce history size

CSV not found → check working directory

🔐 Production Deployment
AWS: Use boto3 + CloudWatch metrics

Azure: ComputeManagementClient, MetricsQueryClient

GCP: monitoring_v3, compute_v1

Persistent storage: SQLite, PostgreSQL

Alerts: Slack or email integration

📚 Related Technologies
AWS CloudWatch

Prometheus + Grafana

Datadog

Kubernetes HPA

Terraform

📈 Performance Metrics
Monitoring frequency: 2s (configurable)

Scaling decision time: <1s

Max resources: 10 (default)

History: 50 points

Memory usage: <50 MB

🎯 Interview Questions Covered
What is auto-scaling and why is it important?

How do you set scaling thresholds?

How do you prevent scaling thrashing?

Horizontal vs vertical scaling?

How do you calculate cost savings?

🤝 Enhancement Ideas
Predictive scaling with ML

Multi-metric scaling

REST API for external tools

Spot/preemptible instance simulation

Anomaly detection

Cost estimation dashboard

📝 License
MIT License – free for educational and commercial use.

👨‍💻 Author
DevOps Engineering Team

🙏 Acknowledgments
Inspired by AWS Auto Scaling, Azure VM Scale Sets, and GCP Managed Instance Groups.
