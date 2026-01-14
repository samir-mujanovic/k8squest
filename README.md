# K8sQuest 🕹️⚙️

[![Platform Support](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-blue)]()
[![Shell](https://img.shields.io/badge/shell-bash-green)]()
[![Kubernetes](https://img.shields.io/badge/kubernetes-learning-326CE5)]()

Learn Kubernetes by fixing it.

K8sQuest is a **local, game-based Kubernetes training platform** with an interactive GUI-like terminal interface. Each mission breaks something in Kubernetes. Your job is to fix it.

**50 progressive challenges across 5 worlds** - from beginner to advanced.

No cloud. No AWS. No costs.

## Features

- 📊 **Real-time Monitoring** - Watch Kubernetes resources update live with "check" command
- 💡 **Progressive Hints** - Unlocks gradually as you need help
- 📚 **Step-by-Step Guides** - Beginner-friendly walkthroughs when you need them
- **Post-Mission Debriefs** - Learn WHY your fix worked with real-world examples
- 🎯 **Clear Mission Briefings** - Know difficulty, time estimate, and concepts
- 🏆 **XP & Progress System** - Track your learning journey and achievements
- 🎮 **Multi-Terminal Workflow** - Learn real-world debugging patterns
- 💾 **Auto-Save Progress** - Never lose your achievements
- 🔄 **Reset Levels** - Get stuck? Clean slate anytime

## 🛡️ Safety First

K8sQuest includes **comprehensive safety guards** (enabled by default):
- ✅ Prevents deletion of critical namespaces (kube-system, default, etc.)
- ✅ Blocks destructive cluster-wide operations
- ✅ Limits operations to `k8squest` namespace via RBAC
- ✅ Confirms risky operations before execution
- ✅ Safe for beginners - hard to break things!

[Learn more about safety guards →](docs/SAFETY.md)

## Requirements
- Docker Desktop (running)
- kubectl
- kind
- bash
- python3
- jq

## Platform Support

K8sQuest works on **Linux, macOS, and Windows**!

- ✅ **Linux** - Native bash support
- ✅ **macOS** - Native bash support  
- ✅ **Windows** - Requires Git Bash (see Windows installation below)

## Installation

### Linux & macOS

Quick setup - just run:
```bash
./install.sh
```

### Windows Installation

K8sQuest supports Windows! Follow these steps:

#### Prerequisites

1. **Docker Desktop** - [Download](https://www.docker.com/products/docker-desktop/)
   - Install and enable WSL2 backend (recommended)
   - **Start Docker Desktop** before running K8sQuest

2. **Git for Windows** - [Download](https://git-scm.com/download/win)
   - ✅ Includes Git Bash (required!)
   - ✅ Includes essential Unix utilities
   - **Important:** Always use Git Bash, not PowerShell or CMD

3. **kubectl** - Choose one installation method:
   ```bash
   # Option 1: Using Chocolatey (in PowerShell as Admin)
   choco install kubernetes-cli
   
   # Option 2: Using Scoop
   scoop install kubectl
   
   # Option 3: Manual download
   # Visit: https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/
   ```

4. **Kind** - Choose one installation method:
   ```bash
   # Option 1: Using Chocolatey (in PowerShell as Admin)
   choco install kind
   
   # Option 2: Using Scoop
   scoop install kind
   
   # Option 3: Using Go (if you have Go installed)
   go install sigs.k8s.io/kind@latest
   ```

5. **Python 3.8+**
   - **Recommended:** Microsoft Store (search "Python")
   - Or download from [python.org](https://www.python.org/downloads/windows/)

6. **jq** ( Required for advanced )
   ```bash
   # Option 1: Using Chocolatey
   choco install jq
   
   # Option 2: Using Scoop
   scoop install jq
   ```

#### Running on Windows

⚠️ **CRITICAL:** Always use **Git Bash**, not PowerShell or CMD!

```bash
# 1. Open Git Bash (not PowerShell/CMD!)
# 2. Clone the repository
git clone https://github.com/Manoj-engineer/k8squest.git
cd k8squest

# 3. Run installation
./install.sh

# 4. Start playing
./play.sh
```

#### Windows Troubleshooting

**Issue:** `bash: command not found`
- **Solution:** Make sure you're using Git Bash, not PowerShell or CMD

**Issue:** `docker: command not found`  
- **Solution:** Start Docker Desktop and wait until it's fully running

**Issue:** Scripts show `^M` errors  
- **Solution:** This is fixed by `.gitattributes`, but if you still see it:
  ```bash
  git config core.autocrlf input
  git rm --cached -r .
  git reset --hard
  ```
#### Alternative: WSL2

For the best experience on Windows, use Windows Subsystem for Linux:

```bash
# In PowerShell (as Administrator)
wsl --install -d Ubuntu

# Then restart your computer and use Ubuntu terminal for K8sQuest
```

This provides a native Linux environment and the smoothest experience.

## Quick Start
```bash
# One-time setup
./install.sh

# Start playing
./play.sh
```

## 🎮 How to Play

1. **Start the game** - Run `./play.sh` (keeps the game running)
2. **Read the mission briefing** - Understand what's broken  
3. **OPEN A NEW TERMINAL** ⚠️ - Keep the game running in the first terminal!
4. **Use kubectl to investigate** - Check pods, logs, and events in the NEW terminal
5. **Fix the issue** - Apply corrections using kubectl commands
6. **Return to game terminal** - Choose an action (check/validate/guide)
7. **Earn XP** - Complete missions to level up!

## 🎯 Available Commands During Play

- `check` - Monitor resource status in real-time (watch for changes!)
- `guide` - Show step-by-step solution walkthrough *(Coming soon - will be updated in future)*
- `hints` - Display progressive hints (unlocks more on each use)
- `solution` - View the solution.yaml file
- `validate` - Test if your solution works
- `skip` - Skip to the next level (no XP awarded)
- `quit` - Exit the game (progress is auto-saved)

## 🎓 Post-Mission Debriefs

After completing each mission, you'll get a detailed debrief explaining:
- ✅ What actually happened and why
- 🧠 The correct mental model for this concept
- 🚨 Real-world production incident examples
- 💼 Interview questions you can now answer
- 🔧 kubectl commands you mastered

**This is where the real learning happens!**

## 🔧 Reset Levels

Get stuck or want to retry? Reset any level from any world:
```bash
# First, activate the virtual environment
source venv/bin/activate

# Reset levels from any world
python3 engine/reset.py level-1-pods                # World 1
python3 engine/reset.py level-15-rollout            # World 2
python3 engine/reset.py level-28-endpoints          # World 3
python3 engine/reset.py level-38-volume-permissions # World 4
python3 engine/reset.py level-45-node-affinity      # World 5
```

Or reset everything:
```bash
python3 engine/reset.py all
```

## 📚 Learning Path

### 🎯 World 1: Core Kubernetes Basics (Levels 1-10) 
**Difficulty**: Beginner | **Total XP**: 1,000  
Master the fundamentals of Kubernetes debugging and troubleshooting.

- ✅ Level 1: CrashLoopBackOff Challenge (100 XP)
- ✅ Level 2: Deployment Zero Replicas (100 XP)
- ✅ Level 3: ImagePullBackOff Mystery (100 XP)
- ✅ Level 4: Pending Pod Problem (100 XP)
- ✅ Level 5: Lost Connection - Labels & Selectors (100 XP)
- ✅ Level 6: Port Mismatch Mayhem (100 XP)
- ✅ Level 7: Sidecar Sabotage (100 XP)
- ✅ Level 8: Pod Logs Mystery (100 XP)
- ✅ Level 9: Init Container Gridlock (100 XP)
- ✅ Level 10: Namespace Confusion (100 XP)

### 🏆 World 2: Deployments & Scaling (Levels 11-20) 
**Difficulty**: Intermediate | **Total XP**: 1,350  
Master deployment strategies, scaling, and health checks.

- ✅ Rolling updates, rollbacks, HPA, liveness/readiness probes
- ✅ PodDisruptionBudgets, canary deployments, anti-affinity
- ✅ Resource management, pod lifecycle, and production patterns

### 🏆 World 3: Networking & Services (Levels 21-30) 
**Difficulty**: Intermediate | **Total XP**: 2,100  
Master service discovery, load balancing, and network policies.

- ✅ ClusterIP, NodePort, LoadBalancer services
- ✅ DNS resolution, Ingress controllers, NetworkPolicies
- ✅ Session affinity, cross-namespace communication, headless services

### 🏆 World 4: Storage & Stateful Apps (Levels 31-40) 
**Difficulty**: Advanced | **Total XP**: 2,600  
Master persistent storage, StatefulSets, and configuration management.

- ✅ PersistentVolumes, PVCs, access modes, StorageClasses
- ✅ StatefulSets, volume permissions, reclaim policies
- ✅ ConfigMaps, Secrets, and production storage patterns

### 🏆 World 5: Security & Production Ops (Levels 41-50) 
**Difficulty**: Advanced | **Total XP**: 3,150  
Production-ready Kubernetes: RBAC, security, resource management, and chaos engineering.

- ✅ RBAC (ServiceAccounts, Roles, RoleBindings)
- ✅ SecurityContext, Pod Security Standards (restricted)
- ✅ ResourceQuotas, NetworkPolicies, node scheduling
- ✅ Taints/Tolerations, PodDisruptionBudgets, PriorityClass
- ✅ **Level 50**: 🔥 **The Chaos Finale** - 9 simultaneous failures in a production scenario!

**Total Journey**: 50 Levels | 10,200 XP | Beginner → Kubernetes Master 🏆

📖 **Full Blueprint**: See [docs/50-CHALLENGE-BLUEPRINT.md](docs/50-CHALLENGE-BLUEPRINT.md) for detailed descriptions of all 50 challenges.


## 🛠️ Manual Play (Advanced)

If you prefer the old-school bash script:
```bash
./engine/start_game.sh
```

## ⭐ Support the Project

If K8sQuest helped you learn Kubernetes, please consider:

- **⭐ Star this repo** - Help others discover this free resource!
- **🐦 Share** - Tell your teammates and friends about it
- **💬 Feedback** - Open an issue with suggestions or bugs
- **🤝 Contribute** - Add new levels or improve existing ones

Your support helps keep this project free and accessible to everyone learning Kubernetes! 

## 📖 Contributing

Want to add more missions? Check out [docs/contributing.md](docs/contributing.md)
