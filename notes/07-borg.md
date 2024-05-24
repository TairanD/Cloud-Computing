# Borg

This lecture introduces Borg, Google's cluster management software, designed to efficiently manage large-scale 
distributed workloads, ensure high reliability, and abstract resource management and failure handling from users.

## 1 Cluster Management with Borg

### 1.1 - Design Goals
- Manage Large Workloads: Efficiently handle jobs distributed across many machines with high reliability and availability.
- Abstract Resource Management: Hide complexities of **resource management** and **failure handling** from users, allowing them 
to focus on application development. This is important as the **machines of a cluster differ** in terms of several aspects.
- Support Diverse Jobs: Handle both long-running, highly dependable production jobs and non-production batch jobs.

### 1.2 - Borg Organization
Borg Cluster: Consists of tens of thousands of interconnected machines.
Cell: A manageable subset of the cluster.
BorgMaster: A centralized controller with five replicas.
Borglets: Processes on each machine that manage tasks and local resources.

### 1.3 - BorgMaster Functions
1. Handles client RPCs.
2. Manages state machines for system objects.
3. Communicates with Borglets.
4. Responds to web-based interface requests.

### 1.4 - Task State Changes

Triggered by user actions (submit, kill, update) or system actions (reject, evict, lose).


## 2 - Borg Scheduler

### 2.1 - Scheduler Functions
- **Periodically scans** a **priority queue** of pending tasks in a **round-robin** order.
- Feasibility component **locates suitable systems**.
- Scoring component identifies the best machine for the task.