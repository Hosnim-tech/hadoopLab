# Hadoop Lab (Docker)

## Prerequisites

Install:

* Docker Desktop (Windows/macOS)

Make sure Docker is running.

---

## Clone the project

```bash
git clone https://github.com/YOUR_USERNAME/hadoop-lab.git
cd hadoop-lab
```

---

## Start the cluster

```bash
docker compose up -d
```

---

## Enter the namenode

```bash
docker exec -it namenode bash
```

---

## Verify Hadoop

```bash
jps
hdfs dfsadmin -report
```

---

## Web interfaces

* HDFS: http://localhost:9870
* YARN: http://localhost:8088

---

## Stop the cluster

```bash
docker compose down
```
