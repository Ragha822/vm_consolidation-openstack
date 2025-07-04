# 🖥️ VM Consolidation with Workload Prediction and ILP Optimization

This project implements a VM consolidation framework in an OpenStack environment to improve resource utilization and energy efficiency. It predicts workloads using GRU-based deep learning models and uses Integer Linear Programming (ILP) for optimal VM migration decisions across compute nodes.

## 📌 Project Goals

- Predict future CPU usage of VMs using GRU models.
- Minimize active hosts through intelligent VM consolidation.
- Improve energy efficiency and load balancing in cloud environments.
- Reduce SLA violations by avoiding overloading target hosts.

---

## ⚙️ Architecture Overview

             ┌────────────┐
             │  OpenStack │
             │ Environment│
             └────┬───────┘
                  │
          ┌───────▼────────┐
          │ VM Workload    │
          │ Data Collector │
          └───────┬────────┘
                  │
          ┌───────▼────────┐
          │ GRU Model      │◄────── Historical CPU Usage
          │ (Prediction)   │
          └───────┬────────┘
                  │
          ┌───────▼────────┐
          │ ILP Optimizer  │◄──── VM resource matrix
          │ (Migration Plan) │
          └───────┬────────┘
                  │
          ┌───────▼────────┐
          │ VM Migrator    │───▶ OpenStack Compute Nodes
          └────────────────┘




---

## 🛠️ Tech Stack

- **OpenStack** (multi-node setup: controller, compute, network)
- **Python** for orchestration and modeling
- **TensorFlow/Keras** for GRU model
- **PuLP / Google OR-Tools** for ILP formulation
- **Prometheus / Libvirt / Custom Scripts** for data collection
- **Grafana** (optional) for visualization

---

## 📂 Directory Structure


├── data/
│ └── collected_usage.csv
├── models/
│ └── gru_model.h5
├── optimizer/
│ └── ilp_solver.py
├── migrator/
│ └── vm_migrator.py
├── predictor/
│ └── workload_predictor.py
├── openstack_scripts/
│ ├── fetch_usage.py
│ └── live_migrate.py
├── notebooks/
│ └── model_training.ipynb
├── README.md
└── requirements.txt
