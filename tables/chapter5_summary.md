# Table 2: Summary of Migration Challenges & Mitigations (Chapter 5)

This table focuses on the operational and technical challenges identified in Chapter 5 that often accompany the migration from a FaaS (AWS Lambda) model to an IaaS (monolithic on EC2) model. For each potential difficulty, it provides suggested strategies to mitigate the risks or drawbacks.

*   **Challenge:** Identifies a specific potential problem or downside associated with moving to and operating an IaaS-based monolith.
*   **Description:** Provides a brief explanation of *why* the item is considered a challenge, often contrasting it with the managed nature of FaaS.
*   **Proposed Mitigation Strategies:** Lists techniques, tools or operational practices that can help overcome or reduce the impact of the corresponding challenge.

| Challenge                                   | Description                                                                          | Proposed Mitigation Strategies                                                                                                |
| :------------------------------------------ | :----------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------- |
| **Downtime During System Updates**          | Monolith updates are riskier; failure can affect the entire application.             | Implementing safe deployment strategies (e.g., "Blue/Green") with robust rollback capabilities.                  |
| **Increased Operational Costs (Management & Maintenance)** | IaaS requires managing infrastructure (OS patching, configuration, etc.).          | Infrastructure as Code (IaC), Auto Scaling, Automated Monitoring & Alerting.         |
| **Resource Underutilization (Horizontal Scaling)** | Scaling potentially leads to underutilized resources if demand falls between scaling thresholds. | Utilize smaller instance types for scaling increments to achieve finer granularity and better match capacity to demand fluctuations. |            |
| **Increased Provisioning Time (Horizontal Scaling)** | IaaS instances take longer to provision than FaaS functions, impacting responsiveness to spikes. | Predictive Scaling combined with Dynamic Scaling; `AMI` Optimization (pre-baking dependencies).                               |
| **Increased Security Risks**                | IaaS exposes more attack surface (OS, direct access, firewall misconfigurations) compared to FaaS sandbox. | Reverse Proxy (`Amazon Elastic Load Balancing`, NGINX), Automated OS Patching (e.g., `AWS Systems Manager`), Regular Dependency Updates, Automated Code Security Analysis, Secure SSH Access (or disable). |