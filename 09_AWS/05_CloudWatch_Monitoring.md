# CloudWatch Monitoring

---

## Introduction

`Amazon CloudWatch` is a monitoring and observability service used to track the performance and health of AWS resources.

CloudWatch collects metrics, logs, and events from services such as EC2, RDS, and load balancers, allowing engineers to monitor infrastructure in real time.

CloudWatch helps with:

- Performance monitoring
- Alerting and notifications
- Infrastructure observability
- Automated scaling triggers

---

## CloudWatch Metrics

Metrics are time-ordered data points representing the performance of AWS resources.

For EC2 instances, CloudWatch automatically collects several system metrics.

Common EC2 metrics include:

| Metric | Description |
|------|-------------|
| CPUUtilization | Percentage of CPU capacity being used |
| NetworkIn | Incoming network traffic |
| NetworkOut | Outgoing network traffic |
| DiskReadOps | Disk read operations |
| DiskWriteOps | Disk write operations |
| StatusCheckFailed | Indicates instance health issues |

These metrics allow engineers to analyze system performance and detect abnormal behavior.

---

## CloudWatch Alarms

A `CloudWatch Alarm` monitors a metric and triggers an action when a defined threshold is exceeded.

Example alarm condition:

```
CPUUtilization > 70%
```

Possible actions triggered by alarms include:

- Sending notifications
- Triggering Auto Scaling policies
- Executing automated responses

Alarms are commonly used to detect performance issues in production environments.

---

## Hands-on: Monitoring EC2 CPU Usage

To understand how monitoring and alerting works, a CPU load experiment was performed on an EC2 instance.

### Steps Performed

1. Launched an EC2 instance.
2. Connected to the instance using SSH.
3. Installed the `stress` tool to generate CPU load.
4. Observed CPU utilization metrics in CloudWatch.
5. Created an alarm based on CPU usage.

---

## Installing Stress Tool

The `stress` utility was installed to simulate heavy CPU usage on the instance.

Example commands:

```bash
sudo yum install stress -y
```

To generate CPU load:

```bash
stress --cpu 2 --timeout 300
```

Explanation:

| Parameter | Meaning |
|----------|---------|
| `--cpu 2` | Creates two CPU workers |
| `--timeout 300` | Runs the workload for 5 minutes |

This artificial workload increases CPU utilization so the monitoring system can detect it.

---

## Observing Metrics in CloudWatch

While the `stress` command was running, the following metric was observed in CloudWatch:

```
CPUUtilization
```

The CPU graph increased significantly during the stress test, confirming that CloudWatch was collecting real-time performance data from the EC2 instance.

---

## Creating a CloudWatch Alarm

An alarm was configured using the following parameters:

| Setting | Example Value |
|-------|---------------|
Metric | CPUUtilization |
Threshold | 70% |
Evaluation Period | 5 minutes |
Statistic | Average |

Alarm behavior:

```
CPU Utilization exceeds threshold
        |
CloudWatch Alarm triggered
```

This demonstrates how monitoring systems can detect performance anomalies.

---

## Role of CloudWatch in DevOps

Monitoring is a critical component of modern infrastructure management.

CloudWatch enables:

### Observability

Understanding system behavior through metrics and logs.

### Alerting

Automatically notifying engineers when systems exceed operational thresholds.

### Automation

CloudWatch alarms can trigger automated scaling or recovery actions.

---

## Key Takeaways

During the CloudWatch lab:

- Monitored EC2 performance metrics
- Generated CPU load using the `stress` tool
- Observed metric changes in CloudWatch
- Configured an alarm based on CPU utilization

This experiment demonstrated how monitoring and alerting systems detect performance issues and support automated infrastructure management.
