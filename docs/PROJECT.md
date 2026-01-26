# MCPPlex

A comprehensive orchestration platform that integrates factory management systems with AI-powered agents through Model Context Protocol (MCP) for intelligent automation and monitoring.

---

## 🏗️ Architecture Overview

MCPPlex is a multi-component system that connects factory management applications with an AI orchestrator through dynamically generated MCP servers, providing an intelligent interface for factory operations management.

```
┌─────────────────────────────────────────────────────────────┐
│                         AGUI                                 │
│                  (Agentic UI Interface)                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ↓
┌─────────────────────────────────────────────────────────────┐
│              LangGraph Orchestrator                          │
│            (Agentic AI Application)                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ↓
┌─────────────────────────────────────────────────────────────┐
│                  MCP Spawner                                 │
│         (Dynamic MCP Server Generator)                       │
└────────────────────────┬────────────────────────────────────┘
                         │
          ┌──────────────┴──────────────┐
          ↓                             ↓
┌──────────────────┐         ┌──────────────────┐
│   MRP Service    │         │   PLM Service    │
│   (Port 3001)    │         │   (Port 3000)    │
└──────────────────┘         └──────────────────┘
```

---

## 📦 Components

### 1. Factory Management System

**Description:** Core backend services providing factory operations management.

- **MRP (Maintenance and Resource Planning)** - Port 3001
- **PLM (Production Line Monitoring)** - Port 3000

**Repository:** [factory-management-system](https://git.i.mercedes-benz.com/PATPAVA/factory-management-system)

**Setup:**
```bash
git clone https://git.i.mercedes-benz.com/PATPAVA/factory-management-system
cd factory-management-system
docker-compose up
```

**Services:**
- MRP: `http://localhost:3001`
- PLM: `http://localhost:3000`

---

### 2. MCP Spawner

**Description:** A NestJS-based application that dynamically generates MCP (Model Context Protocol) servers from Swagger/OpenAPI specifications. It automatically creates tools and hosts them for the orchestrator to consume.

**Repository:** [poc-dynamic-mcp-spawning](https://git.i.mercedes-benz.com/PATPAVA/poc-dynamic-mcp-spawning)

**Setup:**
```bash
git clone https://git.i.mercedes-benz.com/PATPAVA/poc-dynamic-mcp-spawning
cd poc-dynamic-mcp-spawning
docker-compose up
```

**Features:**
- Dynamic MCP server generation from JSON/OpenAPI URLs
- Automatic tool creation from API endpoints
- Real-time MCP hosting and management

---

### 3. LangGraph Orchestrator

**Description:** The core AI orchestration engine that coordinates between the MCP servers and manages agentic workflows for factory operations.

**Repository:** [langgraph-orchestrator](https://git.i.mercedes-benz.com/PATPAVA/langgraph-orchestrator)

**Setup:**
```bash
git clone https://git.i.mercedes-benz.com/PATPAVA/langgraph-orchestrator
cd langgraph-orchestrator
.\start.ps1
```

**Capabilities:**
- Multi-agent orchestration
- MCP tool integration
- Workflow automation
- Intelligent decision-making

---

### 4. AGUI (Agentic UI)

**Description:** Modern web interface for interacting with the orchestration layer, providing a user-friendly way to manage and monitor factory operations through AI agents.

**Repository:** [AgUI](https://git.i.mercedes-benz.com/PATPAVA/AgUI)

**Setup:**
```bash
git clone https://git.i.mercedes-benz.com/PATPAVA/AgUI
cd AgUI
docker-compose up -d
```

**Features:**
- Interactive chat interface with AI agents
- Real-time factory monitoring
- Workflow visualization
- Agent status tracking

---

## 🚀 Quick Start Guide

### Prerequisites

- Docker & Docker Compose
- PowerShell (for orchestrator)
- Git
- Network access to internal Mercedes-Benz repositories

### Step-by-Step Setup

#### Step 1: Start Factory Management Services

```bash
# Clone and start MRP & PLM services
git clone https://git.i.mercedes-benz.com/PATPAVA/factory-management-system
cd factory-management-system
docker-compose up
```

Wait for services to be ready:
- MRP: http://localhost:3001
- PLM: http://localhost:3000

#### Step 2: Launch MCP Spawner

```bash
# In a new terminal
git clone https://git.i.mercedes-benz.com/PATPAVA/poc-dynamic-mcp-spawning
cd poc-dynamic-mcp-spawning
docker-compose up
```

#### Step 3: Start Orchestrator

```bash
# In a new terminal
git clone https://git.i.mercedes-benz.com/PATPAVA/langgraph-orchestrator
cd langgraph-orchestrator
.\start.ps1
```

#### Step 4: Launch AGUI

```bash
# In a new terminal
git clone https://git.i.mercedes-benz.com/PATPAVA/AgUI
cd AgUI
docker-compose up -d
```

#### Step 5: Access the Platform

Open your browser and navigate to the AGUI interface (check the AgUI documentation for the specific URL).

---

## 🔧 Configuration

Each component may require specific environment variables or configuration files. Please refer to the individual repositories for detailed configuration instructions:

- [Factory Management System Configuration](https://git.i.mercedes-benz.com/PATPAVA/factory-management-system)
- [MCP Spawner Configuration](https://git.i.mercedes-benz.com/PATPAVA/poc-dynamic-mcp-spawning)
- [Orchestrator Configuration](https://git.i.mercedes-benz.com/PATPAVA/langgraph-orchestrator)
- [AGUI Configuration](https://git.i.mercedes-benz.com/PATPAVA/AgUI)

---

## 🔄 Data Flow

1. **User Interaction** → User interacts through AGUI interface
2. **Orchestration** → LangGraph Orchestrator processes requests and plans actions
3. **Tool Discovery** → Orchestrator queries MCP Spawner for available tools
4. **MCP Generation** → MCP Spawner dynamically generates tools from factory APIs
5. **Execution** → Tools interact with MRP/PLM services
6. **Response** → Results flow back through the chain to AGUI

---

## 📝 Use Cases

- **Predictive Maintenance:** AI agents analyze MRP data to predict maintenance needs
- **Production Optimization:** Real-time monitoring and optimization of production lines
- **Resource Allocation:** Intelligent resource planning based on current and forecasted demand
- **Anomaly Detection:** Automatic detection and alerting of production anomalies
- **Conversational Operations:** Natural language interface for factory management

---

## 🛠️ Technology Stack

- **Backend Services:** Node.js, Docker
- **MCP Spawner:** NestJS, TypeScript
- **Orchestrator:** LangGraph, Python
- **Frontend:** Modern web technologies (see AGUI repo)
- **Containerization:** Docker, Docker Compose
- **AI/ML:** LangGraph, Agent frameworks

---

## 📚 Documentation

For detailed documentation on each component, please visit the respective repositories:

- [Factory Management System Docs](https://git.i.mercedes-benz.com/PATPAVA/factory-management-system)
- [MCP Spawner Docs](https://git.i.mercedes-benz.com/PATPAVA/poc-dynamic-mcp-spawning)
- [LangGraph Orchestrator Docs](https://git.i.mercedes-benz.com/PATPAVA/langgraph-orchestrator)
- [AGUI Docs](https://git.i.mercedes-benz.com/PATPAVA/AgUI)

---

## 🤝 Contributing

This is an internal Mercedes-Benz project. For contribution guidelines, please contact the project maintainers.

---

## 📧 Contact & Support

For questions, issues, or support requests, please reach out to the project team through the internal Mercedes-Benz communication channels.

---

## 📄 License

Internal Mercedes-Benz project. All rights reserved.

---

**Last Updated:** November 23, 2025
