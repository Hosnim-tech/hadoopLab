# Hadoop Lab: Docker-Based HDFS & MapReduce Environment

A self-contained lab environment for learning **Apache Hadoop**, **HDFS**, **YARN**, and **MapReduce** using Docker. No local Hadoop installation required.

---

## Repository Structure

```
hadoopLab/
├── docker-compose.yml      # Cluster definition (1 NameNode + 2 DataNodes)
├── Code/
│   └── WordCount.java      # MapReduce WordCount implementation
├── text.txt                # Sample input file for MapReduce jobs
└── README.md               # This file
```

---

## Architecture

```
┌─────────────────────────────────────────┐
│            Docker Bridge Network        │
│                                         │
│  ┌───────────┐   ┌──────────────────┐   │
│  │ NameNode  │   │   DataNode 1     │   │
│  │           │◄──│                  │   │
│  │ HDFS UI   │   └──────────────────┘   │
│  │ :9870     │                          │
│  │ YARN UI   │   ┌──────────────────┐   │
│  │ :8088     │◄──│   DataNode 2     │   │
│  └───────────┘   │                  │   │
│                  └──────────────────┘   │
└─────────────────────────────────────────┘
```

| Service | URL |
|---|---|
| HDFS NameNode UI | http://localhost:9870 |
| YARN ResourceManager UI | http://localhost:8088 |
| DataNode 1 Info | http://localhost:9870/dfshealth.html |

---

## Prerequisites

| Tool | Version | Download |
|---|---|---|
| Docker Desktop | Latest | https://www.docker.com/products/docker-desktop |
| Git | Any | https://git-scm.com |

> **Windows users:** Make sure to set Git line endings correctly before cloning:
> ```bash
> git config --global core.autocrlf false
> ```

---

## Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/Hosnim-tech/hadoopLab.git
cd hadoopLab
```

### 2. Start the cluster

```bash
docker compose up -d
```

### 3. Verify containers are running

```bash
docker ps
```

You should see three containers: `namenode`, `datanode1`, `datanode2`.

### 4. Enter the NameNode

```bash
docker exec -it namenode bash
```

### 5. Verify the cluster

```bash
# Check running Java processes
jps

# Check HDFS status and DataNodes
hdfs dfsadmin -report
```

### 6. Access the Web UIs

- **HDFS NameNode:** http://localhost:9870
- **YARN ResourceManager:** http://localhost:8088

---

## HDFS Operations

```bash
# Create a directory
hdfs dfs -mkdir -p /input

# Upload a file
hdfs dfs -put /tmp/myfile.txt /input/

# List files
hdfs dfs -ls /input

# Read a file
hdfs dfs -cat /input/myfile.txt

# Check replication
hdfs fsck /input -files -blocks -locations
```
---

## Stop the Cluster

```bash
docker compose down
```

---


