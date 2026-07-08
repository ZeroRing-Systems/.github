<div align="center">
  <h1>🪐 ZeroRing OS</h1>
  <p><strong>The full-stack, WebAssembly-powered micro-kernel operating system for the web.</strong></p>
</div>

<div align="center">
  <!-- TODO: Replace with the actual URL to your uploaded GIF demo -->
  <img src="ZeroRing.gif" alt="ZeroRing Terminal Demo" width="800" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.5);"/>
</div>

<br/>

## 🪐 What is ZeroRing?

ZeroRing is a persistent, fully functional virtual operating system designed to run entirely within your web browser at near-native speeds. 

Built from the ground up, ZeroRing features a custom C++ kernel compiled to WebAssembly (WASM), communicating with a zero-dependency C++ backend via WebSockets. It includes a complete persistent virtual filesystem (VFS) backed by PostgreSQL and supports sandboxed Python execution directly from the shell.

## ✨ Key Features

- **⚡ Blazing Fast WASM Kernel**: A minimalist, custom-built C++ kernel compiled directly to WebAssembly for native-like browser execution.
- **💾 Persistent VFS**: Multi-user isolated filesystem backed by PostgreSQL. Your files, directories, and scripts persist across browser sessions.
- **📝 Built-in UI Editor**: A beautiful integrated code editor (`edit <filename>`) overlaid directly onto the terminal for writing multi-line scripts.
- **🐍 Sandboxed Execution**: Write and execute Python scripts (`run <filename>`) dynamically on the server directly from your browser terminal.
- **🔌 Zero-Dependency C++ Backend**: A highly concurrent, ultra-low latency WebSocket proxy server built from scratch with standard POSIX sockets.

## 🚀 Quick Start

ZeroRing is containerized and orchestrated via Docker Compose, making deployment incredibly easy.

```bash
# Clone the orchestration repository and its submodules
git clone --recurse-submodules https://github.com/ZeroRing-Systems/ZeroRing-Deploy.git
cd ZeroRing-Deploy

# Build and start the cluster
sudo docker compose up --build
```
Navigate to `http://localhost:8080` in your browser to view the landing page and launch the terminal!

## 💻 Available Commands

| Command | Description |
|---|---|
| `edit <file>` | Open the integrated text editor UI |
| `run <file>` | Execute a Python script in the sandbox |
| `cd <path>` | Change the current working directory |
| `ls [path]` | List contents of a directory |
| `mkdir <path>` | Create a new directory |
| `rm <path>` | Remove a file or empty directory |
| `write <f> <d>`| Quickly write data to a file inline |
| `cat <file>` | Print file contents to the terminal |
| `help`, `pwd` | Standard system utilities |

## 🏗️ Architecture

ZeroRing is split across three primary repositories to ensure strict modularity:

1. **[ZeroKernel](https://github.com/ZeroRing-Systems/ZeroKernel)**: The core C++ codebase compiled to WebAssembly. Handles tokenization, command dispatching, path resolution, and JSON packet formatting.
2. **[ZeroRing-Cloud](https://github.com/ZeroRing-Systems/ZeroRing-Cloud)**: The frontend HTML/JS interface and the concurrent C++ WebSocket backend server.
3. **[ZeroRing-Deploy](https://github.com/ZeroRing-Systems/ZeroRing-Deploy)**: The umbrella repository orchestrating the Docker multi-stage builds, PostgreSQL database initialization, and NGINX routing.

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request or open an issue on any of the sub-repositories to help us build the ultimate browser OS.
