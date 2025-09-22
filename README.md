# Edge-based Federated Learning Methods for Remaining Useful Life Estimation in IIoT

This work investigates how **edge computing combined with federated learning (FL)** can improve **Remaining Useful Life (RUL) estimation** in Industrial Internet of Things (IIoT) systems. The goal is to enhance predictive maintenance while preserving data privacy and reducing latency.

### Background
- **Predictive maintenance** forecasts equipment failures, reducing downtime and costs.  
- **RUL estimation** predicts how long a machine component will continue functioning before failure.  
- **Edge computing** processes data closer to the source, reducing latency and bandwidth usage.  
- **Federated learning (FL)** enables collaborative model training across distributed devices without sharing raw data, ensuring privacy.

### Dataset & Preprocessing
- Dataset: **NASA’s CMAPSS** (turbofan engine sensor data).  
- Data split across **10 edge devices** for federated training.  
- Each device trained a **Long Short-Term Memory (LSTM)** model locally.

### Federated Learning Architecture
- Central server coordinates the global LSTM model.  
- Clients (edge devices) train local models → send weights → server aggregates into a global model.  
- **20 communication rounds**, each with 10 training epochs.  
- Aggregation methods tested:  
  - **FedAvg** (weighted averaging of local updates)  
  - **FedProx** (adds proximal term to improve convergence)  
  - **KRUM** (filters out noisy or malicious updates)

### Evaluation
- Metrics: **Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), R²**.  
- **Centralized baseline LSTM** achieved lowest error (MAE = 6.99).  
- **Federated models** were slightly worse but competitive:  
  - FedAvg & FedProx → stable convergence  
  - KRUM → unstable for this dataset  
- After 20 rounds, FL reached an average **MAE = 17.01**.

### Key Findings
1. Centralized models outperform FL, but FL ensures **privacy and scalability**.  
2. **FedAvg** and **FedProx** are reliable aggregation methods.  
3. **KRUM** adds robustness but is less useful for homogeneous datasets.  
4. Edge-based FL enables **real-time, privacy-preserving predictive maintenance**.

### Conclusion
- Federated Learning is a **promising approach** for predictive maintenance in IIoT.  
- It balances **accuracy, privacy, and efficiency**.  
- Future work: improved aggregation methods & real-world deployment.

