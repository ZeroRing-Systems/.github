<div align="center">
  <h1>🪐 ZeroRing OS</h1>
  <p><strong>The full-stack, WebAssembly-powered micro-kernel operating system for the web.</strong></p>
  <br/>
  <a href="https://zeroring-cloud.vercel.app"><img src="https://img.shields.io/badge/🌐_Live_Demo-zeroring--cloud.vercel.app-blue?style=for-the-badge" alt="Live Demo"/></a>
</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/ZeroRing-Systems/.github/main/profile/ZeroRing.gif" alt="ZeroRing Terminal Demo" width="800" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.5);"/>
</div>

<br/>

## 🪐 What is ZeroRing?

ZeroRing is a persistent, fully functional virtual operating system designed to run entirely within your web browser at near-native speeds.

Built from the ground up, ZeroRing features a custom C++ kernel compiled to WebAssembly (WASM), communicating with a zero-dependency C++ backend via secure WebSockets (`wss://`). It includes a complete persistent virtual filesystem (VFS) backed by PostgreSQL, session isolation per user, and supports sandboxed Python execution directly from the shell.

**🌐 Try it now:** [zeroring-cloud.vercel.app](https://zeroring-cloud.vercel.app)

## ✨ Key Features

- **⚡ Blazing Fast WASM Kernel**: A minimalist, custom-built C++ kernel compiled directly to WebAssembly for native-like browser execution.
- **💾 Persistent VFS**: Multi-user isolated filesystem backed by PostgreSQL. Your files, directories, and scripts persist across browser sessions.
- **📝 Built-in UI Editor**: A beautiful integrated code editor (`edit <filename>`) overlaid directly onto the terminal for writing multi-line scripts.
- **🐍 Sandboxed Execution**: Write and execute Python scripts (`run <filename>`) dynamically on the server directly from your browser terminal.
- **🔌 Zero-Dependency C++ Backend**: A highly concurrent, ultra-low latency WebSocket proxy server built from scratch with standard POSIX sockets.
- **🔒 SSL/TLS Secured**: All browser-to-server communication is encrypted via Let's Encrypt certificates.
- **🚀 CI/CD Pipeline**: GitHub Actions auto-deploys the backend on every push. Vercel auto-deploys the frontend.

## 🏗️ Architecture

```
┌─────────────────────────────┐
│   Browser                    │
│                              │
│   terminal.js                │
│     ↕ WASM imports           │
│   kernel.wasm (ZeroKernel)   │
│     ↕ JSON over WebSocket    │
└──────────┬──────────────────┘
           │ wss:// (TLS)
           ▼
┌──────────────────────────────┐
│   Azure VM                    │
│                               │
│   Nginx (SSL termination)     │
│     ↓                         │
│   server (C++17 WebSocket)    │
│     ↓                         │
│   PostgreSQL 16 (VFS store)   │
└──────────────────────────────┘
```

## 💻 Available Commands

| Command | Description |
|---|---|
| `help` | List all available commands |
| `ls [path]` | List contents of a directory |
| `cd <path>` | Change the current working directory |
| `mkdir <path>` | Create a new directory |
| `cat <file>` | Print file contents to the terminal |
| `write <f> <d>` | Quickly write data to a file inline |
| `edit <file>` | Open the integrated text editor UI |
| `run <file>` | Execute a Python script in the sandbox |
| `rm <path>` | Remove a file or empty directory |
| `pwd`, `whoami`, `version` | Standard system utilities |

## 📦 Repositories

| Repository | Description |
|---|---|
| **[ZeroKernel](https://github.com/ZeroRing-Systems/ZeroKernel)** | Custom C++ kernel compiled to WebAssembly. Handles tokenization, command dispatch, path resolution, and JSON packet formatting. |
| **[ZeroRing-Cloud](https://github.com/ZeroRing-Systems/ZeroRing-Cloud)** | Frontend (HTML/JS terminal + WASM loader) and concurrent C++ WebSocket backend server with PostgreSQL VFS. |

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Kernel | C++17 → WebAssembly (Emscripten) |
| Frontend | Vanilla HTML/JS, Web Workers |
| Backend | C++17, POSIX sockets, pthreads |
| Database | PostgreSQL 16 (libpqxx) |
| SSL | Let's Encrypt + Nginx |
| Frontend Hosting | Vercel |
| Backend Hosting | Azure VM (Ubuntu 24.04 LTS) |
| CI/CD | GitHub Actions + Vercel auto-deploy |

## 🚀 Quick Start

**Try it online:** Visit [zeroring-cloud.vercel.app](https://zeroring-cloud.vercel.app) and click **Launch Terminal**.

**Run locally:**
```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/ZeroRing-Systems/ZeroRing-Cloud.git
cd ZeroRing-Cloud

# Build backend
mkdir -p build && cd build
cmake .. -DUSE_POSTGRES=OFF
make -j$(nproc)
./server &

# Serve frontend
cd ../public
python3 -m http.server 8000
# Open http://localhost:8000
```

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request or open an issue on any of the repositories to help us build the ultimate browser OS.
