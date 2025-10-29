## Distributed Server Architecture (large deployments)
- Main Management Server + multiple GPU Inference Servers.
- Parallel inference across GPUs; Management Server orchestrates streams and aggregates analytics in MongoDB.
- Designed for high-volume, high-performance scenarios.

![Alt text](assets/Picture15.png)
