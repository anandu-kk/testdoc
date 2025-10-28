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

## Data Flow
1. Video stream ingestion (camera or VMS)
2. Inference engine processes frames at edge or inference server
3. Analytics and events stored in MongoDB
4. Dashboard and APIs present insights to users and third-party systems
