# Architecture

You can deploy VisionX in two configurations depending on your operational scale.

## Option 1: Single Server Architecture
**Ideal for small sites (up to 15 cameras)**

- All components (Frontend, Backend, Inference, Database) run in one container.
- Supports 6–8 real-time video streams.
- Simple setup and minimal hardware requirements.

**Data Flow**
1. Cameras send live feeds directly to VisionX.
2. The inference engine analyzes streams and generates analytics.
3. Results are stored in MongoDB and displayed in the dashboard.

> 💡 **Tip:** Use this setup for quick pilots or small installations.

---

## Option 2: Distributed Server Architecture
**Ideal for large or multi-site deployments**

- A **Main Management Server** coordinates multiple GPU inference servers.
- Each inference node processes video streams in parallel.
- MongoDB aggregates analytics centrally.

**Key Benefits**
- Handles hundreds of video streams
- Enables real-time analytics at scale
- Centralized management and reporting

> 🧩 **Pro Tip:** Combine distributed inference with role-based dashboards for multi-site visibility.
