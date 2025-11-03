# 🧠 VisionX Platform Installation Guide

## 📋 Prerequisites

### 🖥️ System Requirements
- Ensure **at least 2GB+** of free disk space.
- Ensure **CUDA drivers (for Nvidia GPUs)** or **MPS (for Apple Silicon)** are installed and configured.

### 🔐 OpenVPN Access
- Install and configure **OpenVPN** to gain access to the **VisionX Backend**.

### 🧩 Software Requirements
| Software | Version | Notes |
|-----------|----------|-------|
| **Anaconda** | Latest | For managing Python environments |
| **Python** | 3.10 or 3.11 | To be used within Conda |
| **Node.js** | 18+ | Required for frontend and backend |
| **Git** | Latest | For cloning repositories |

---

## ⚙️ Step-by-Step Installation

### 1️⃣ Clone the Repositories

Create a folder for the VisionX platform, open **Command Prompt** in that folder, and clone the required repositories.

#### Frontend
```bash
git clone -b socket_testing https://github.com/mdfawaz1/visionx-Interface.git
```

#### Backend
```bash
git clone -b architecture_v0.1 http://source.iviva.com/Fawaz/ai-platform.git
```

---

### 2️⃣ Set Up the Backend

Navigate to the backend directory:
```bash
cd ai-platform
```

Create and activate a Conda environment:
```bash
conda create --name vision_env python=3.10 -y
conda activate vision_env
```

Install required Python dependencies:
```bash
pip install -r requirements.txt
```

Install Node modules:
```bash
npm install
```

---

### 3️⃣ Set Up the Frontend

Navigate to the frontend directory:
```bash
cd ../visionx-Interface
```

Install Node modules:
```bash
npm install
```

---

### 4️⃣ Start the VisionX Platform

To simplify running all services, create a **Node.js startup script**.  
Save the following as **`start-visionx.js`** in the **root directory** (where both `ai-platform` and `visionx-Interface` are located):

```js
const { exec } = require('child_process');

// Function to run a command in a new terminal
const runCommand = (command, cwd, env) => {
  const fullCommand = `start cmd /k "cd /d ${cwd} && ${env || ''} ${command}"`;
  exec(fullCommand, (err) => {
    if (err) {
      console.error(`Failed to start process in ${cwd}:`, err);
    } else {
      console.log(`Started process in ${cwd}`);
    }
  });
};

// Start the backend
runCommand('npm start', './ai-platform', 'conda activate vision_env &&');

// Start the Python service
runCommand('python service.py', './ai-platform/src/python-service', 'conda activate vision_env &&');

// Start the frontend
runCommand('npm start', './visionx-Interface');
```

---

### ▶️ Steps to Run the Script

1. Ensure all setup steps (backend & frontend) are **complete**.  
2. Save the above script as **`start-visionx.js`** in the **root directory**.  
3. Run the script using Node.js:

   ```bash
   node start-visionx.js
   ```

This will open **three terminal windows**:
- One for the **backend**
- One for the **Python service**
- One for the **frontend**

---

## 🧾 Additional Notes

- Ensure **all dependencies** are correctly installed in both frontend and backend directories.
- Verify that **Python** and **Node.js** versions meet the specified requirements.
- If you encounter issues:
  - Double-check folder paths.
  - Reconfirm Conda environment activation.
  - Ensure VPN access to the backend is active.

---

✅ By following this guide, you should be able to **successfully install and run the VisionX Platform**.
