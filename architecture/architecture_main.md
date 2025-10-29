# Architecture

VisionX supports two deployment topologies:

## Single Server Architecture (up to ~15 cameras / small deployments)
- All-in-one container: frontend UI, management server, inference engine, MongoDB.
- Suitable for small sites; handles real-time for ~6–8 streams reliably.
- Video input from cameras or VMS systems.

## Distributed Server Architecture (large deployments)
- Main Management Server + multiple GPU Inference Servers.
- Parallel inference across GPUs; Management Server orchestrates streams and aggregates analytics in MongoDB.
- Designed for high-volume, high-performance scenarios.

