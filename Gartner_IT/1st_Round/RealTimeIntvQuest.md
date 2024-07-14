## Real-Time Interview Questions for 4 Years Experience at CITI Bank

### Technology Used:
1. AWS
2. Kubernetes
3. Terraform
4. Jenkins
5. Security (IAM)

### AWS (Amazon Web Services):

1. **Migration to AWS**:
   - **Question**: CITI Bank is planning to migrate its legacy infrastructure to AWS. How would you approach the migration, considering factors like data security, compliance, and minimal disruption to services?
   - **Answer**: To approach the migration, I would first conduct a thorough assessment of the existing infrastructure, identify dependencies, and create a detailed migration plan. This includes defining security and compliance requirements, setting up a secure AWS environment, using AWS tools like AWS Database Migration Service (DMS) and AWS Server Migration Service (SMS), and conducting phased migration to minimize disruption. Regular testing and validation at each stage ensure data integrity and service continuity.

2. **Troubleshooting Unresponsive EC2 Instance**:
   - **Question**: Describe an incident where an AWS EC2 instance in a critical application’s auto-scaling group became unresponsive. How would you troubleshoot and restore service quickly?
   - **Answer**: To troubleshoot, I would first check the instance status using AWS Management Console or CLI. Reviewing CloudWatch metrics and logs helps identify resource issues or application errors. I would attempt to connect via SSH to investigate further. If the instance is unresponsive, I would terminate it and rely on the auto-scaling group to launch a new instance automatically, ensuring minimal downtime.

3. **Cost Optimization**:
   - **Question**: CITI Bank is concerned about cost optimization in AWS. Explain some strategies you would implement to ensure cost-effective resource utilization.
   - **Answer**: Strategies include right-sizing instances, using Reserved Instances and Savings Plans, leveraging spot instances for non-critical workloads, implementing auto-scaling, monitoring with AWS Cost Explorer, and using AWS Trusted Advisor for recommendations. Also, optimizing storage with lifecycle policies and leveraging serverless architectures like Lambda can help reduce costs.

4. **Disaster Recovery (DR)**:
   - **Question**: CITI Bank is planning to implement disaster recovery (DR) for its critical applications in AWS. How would you design a resilient and cost-effective DR solution?
   - **Answer**: I would design a DR solution using AWS services like AWS Elastic Disaster Recovery (DRS), S3 for backup storage, and RDS cross-region replication. Implementing a multi-region architecture with failover capabilities ensures high availability. Automating DR drills and using infrastructure as code (IaC) with Terraform ensures consistency and quick recovery.

5. **Serverless Architecture**:
   - **Question**: There’s a need to implement a serverless architecture for certain CITI Bank services. Explain how you would leverage AWS Lambda and other serverless components.
   - **Answer**: I would use AWS Lambda for compute, API Gateway for creating RESTful APIs, and DynamoDB or S3 for storage. Lambda functions can be triggered by events such as API requests, S3 uploads, or DynamoDB updates. Utilizing CloudFormation or Terraform for IaC ensures scalable and manageable serverless deployments.

6. **Enhancing Security**:
   - **Question**: CITI Bank wants to enhance its security posture on AWS. What AWS services and features would you recommend to improve security, especially in a financial institution?
   - **Answer**: I would recommend using AWS IAM for access control, AWS KMS for key management, AWS Config for compliance monitoring, and AWS CloudTrail for auditing. Implementing multi-factor authentication (MFA), VPC with private subnets, security groups, and network ACLs enhances security. Regular security assessments using AWS Inspector and GuardDuty ensure continuous monitoring.

### Kubernetes:

1. **Kubernetes Architecture**:
   - **Question**: CITI Bank wants to deploy a microservices-based application on Kubernetes for improved scalability. How would you design the Kubernetes architecture to ensure high availability and efficient resource utilization?
   - **Answer**: I would design a multi-node Kubernetes cluster with master and worker nodes across multiple availability zones for high availability. Implementing Horizontal Pod Autoscaling ensures efficient resource utilization. Using Kubernetes namespaces isolates environments, and network policies ensure secure communication. Monitoring with Prometheus and Grafana provides insights into cluster performance.

2. **Canary Deployments**:
   - **Question**: Discuss the implementation of Canary deployments in Kubernetes for a critical banking application. How would you monitor and roll back in case of issues?
   - **Answer**: I would use Kubernetes Deployments and Istio or Linkerd for traffic management to implement Canary deployments. Deploying a small percentage of traffic to new versions and monitoring with Prometheus and Grafana ensures safe rollouts. If issues arise, automated rollback strategies and continuous monitoring help revert to stable versions.

3. **Patching Security Vulnerabilities**:
   - **Question**: An application deployed on Kubernetes is facing a security vulnerability. Outline the steps you would take to patch and secure the Kubernetes cluster and applications.
   - **Answer**: First, I would identify and isolate the affected components. Patching involves updating the vulnerable images and redeploying the applications. Applying Kubernetes security best practices like Pod Security Policies, Network Policies, and RBAC ensures cluster security. Regular scanning with tools like Trivy and monitoring with Falco provides ongoing security assurance.

4. **Cluster Upgrade**:
   - **Question**: The CITI Bank Kubernetes cluster needs to be upgraded to a newer version. Outline the steps you would take to perform a safe and seamless upgrade.
   - **Answer**: I would first review the Kubernetes release notes and test the upgrade process in a staging environment. Using tools like kubeadm or managed services like EKS, I would perform a phased upgrade, starting with the control plane and then the worker nodes. Ensuring backups and monitoring during the process helps mitigate issues.

5. **Using Helm**:
   - **Question**: CITI Bank is exploring the use of Helm for managing Kubernetes applications. How would you use Helm to deploy and manage applications in a secure and scalable way?
   - **Answer**: I would use Helm charts to define, install, and upgrade applications, ensuring consistency and repeatability. Versioning Helm charts and using Helm repositories facilitates deployment management. Implementing RBAC for Helm ensures secure deployment, and using values files customizes deployments for different environments.

6. **Resource Leak Detection**:
   - **Question**: Discuss a scenario where a Kubernetes pod running a critical banking application experiences a resource leak. How would you detect and mitigate this issue?
   - **Answer**: I would use monitoring tools like Prometheus and Grafana to detect resource leaks by setting up alerts for abnormal resource usage. Implementing resource requests and limits in the Pod specifications prevents resource exhaustion. Analyzing logs with tools like ELK Stack helps identify the root cause, and automated remediation scripts can restart affected pods.

### Terraform:

1. **Multi-Region Infrastructure**:
   - **Question**: CITI Bank is expanding its services and needs to provision infrastructure in multiple AWS regions using Terraform. How would you structure the Terraform configuration to achieve this efficiently?
   - **Answer**: I would use Terraform modules to encapsulate common configurations and variables to parameterize region-specific settings. Using workspaces or separate state files for each region ensures isolated environments. The directory structure would reflect regions, and remote state storage with S3 and DynamoDB for locking ensures state consistency.

2. **Managing State Files**:
   - **Question**: Explain how you would manage state files in Terraform for a collaborative environment with multiple DevOps engineers working on the same project.
   - **Answer**: I would use remote state storage solutions like AWS S3 with DynamoDB for state locking. This ensures that the state file is centralized and locked during updates, preventing conflicts. Implementing access controls and using versioning for state files helps manage changes and rollbacks.

3. **Multi-Cloud Deployments**:
   - **Question**: CITI Bank is adopting a multi-cloud strategy, including AWS and Azure. How would you design Terraform configurations to support multi-cloud deployments?
   - **Answer**: I would use separate provider configurations for AWS and Azure within the same Terraform project. Modules would encapsulate cloud-specific resources, and shared configurations would use variables and locals for flexibility. Using a consistent naming convention and remote state storage for each cloud provider ensures manageability.

4. **Preventing Unexpected Changes**:
   - **Question**: An unexpected change was made to the production infrastructure using Terraform, causing downtime. How would you prevent such incidents in the future, and what measures would you take to recover quickly?
   - **Answer**: Implementing code review processes with version control and requiring approval for changes ensures oversight. Using `terraform plan` and automated testing before applying changes helps catch issues early. In case of downtime, using backups and having a well-documented recovery plan ensures quick restoration.

### Jenkins (CI/CD):

1. **Handling Diverse Technology Stack**:
   - **Question**: CITI Bank has a diverse set of applications, including Java, .NET, and Python-based. How would you design a Jenkins pipeline that can handle the diverse technology stack efficiently?
   - **Answer**: I would use Jenkins pipelines with stages that accommodate each technology stack. Using Docker containers or agents with specific environments ensures consistency. Parameterized builds and shared libraries for common tasks streamline the process.

2. **Jenkins as Code**:
   - **Question**: Discuss the implementation of Jenkins as a code pipeline. How would you version control Jenkins configurations and ensure consistency across environments?
   - **Answer**: Using Jenkins Job DSL or Jenkinsfile for pipeline definitions and storing them in a version control system ensures consistency. Automating Jenkins setup with tools like Jenkins Configuration as Code (JCasC) and maintaining separate configurations for different environments ensures reliable deployments.

3. **Continuous Security Integration**:
   - **Question**: CITI Bank is emphasizing continuous security integration in

 Jenkins. Explain how you would integrate security scanning tools into the CI/CD pipeline.
   - **Answer**: Integrating security tools like SonarQube for code analysis, OWASP ZAP for dynamic application security testing, and Snyk for dependency scanning ensures continuous security checks. Using Jenkins stages to run these tools and enforcing quality gates prevents insecure code from progressing.

4. **Managing Multiple Environments**:
   - **Question**: CITI Bank has a complex deployment process involving multiple environments (dev, test, prod). How would you design and manage Jenkins pipelines to handle these environments efficiently?
   - **Answer**: Using Jenkins multibranch pipelines or parameterized builds, I would define separate stages for each environment. Implementing environment-specific configurations and using shared libraries for common tasks ensures consistency. Automating promotion between environments based on predefined criteria streamlines the process.

5. **Automated Code Quality Checks**:
   - **Question**: Describe a scenario where a Jenkins build pipeline failed due to a code quality issue. How would you integrate automated code quality checks into the pipeline?
   - **Answer**: Using tools like SonarQube or ESLint integrated into the Jenkins pipeline, I would set up stages for code quality analysis. Enforcing quality gates ensures that code does not proceed if it fails to meet standards. Providing detailed feedback to developers helps address issues promptly.

6. **Blue-Green Deployments**:
   - **Question**: CITI Bank wants to implement blue-green deployments with Jenkins for its critical applications. How would you design and execute such deployments?
   - **Answer**: I would create separate environments for blue and green deployments, ensuring that one serves live traffic while the other is updated. Using Jenkins pipelines, I would automate the deployment process, switching traffic using DNS or load balancers once validation is complete. Monitoring and automated rollback strategies ensure reliability.

### Security (IAM):

1. **IAM Strategy**:
   - **Question**: Define a robust IAM (Identity and Access Management) strategy for CITI Bank’s AWS environment. How would you ensure least privilege access and monitor for any unauthorized activities?
   - **Answer**: Implementing a role-based access control (RBAC) model with IAM roles and policies ensures least privilege access. Using AWS Organizations and Service Control Policies (SCPs) enforces account-level restrictions. Monitoring with CloudTrail and AWS Config, and integrating with SIEM tools, ensures continuous security oversight.

2. **Revoking Access**:
   - **Question**: An employee is leaving CITI Bank, and their access needs to be revoked across AWS resources. Describe the steps you would take to ensure timely and secure access removal.
   - **Answer**: Using IAM user management, I would disable the employee’s account and remove access keys and roles. Reviewing CloudTrail logs ensures no ongoing sessions. Automating the process with IAM policies and integrating with HR systems ensures timely and secure access removal.

3. **Zero Trust Security Model**:
   - **Question**: CITI Bank is implementing a Zero Trust Security model. How would you apply this model to IAM in AWS, and what measures would you take to enhance security?
   - **Answer**: Implementing a Zero Trust model involves enforcing strict identity verification and access controls. Using IAM roles, policies, and least privilege principles, I would ensure granular access control. Implementing multi-factor authentication (MFA), monitoring with CloudTrail, and using AWS Secrets Manager for secure credential management enhances security.

4. **Multi-Factor Authentication (MFA)**:
   - **Question**: CITI Bank is considering multi-factor authentication (MFA) for AWS IAM users. Explain how you would implement and enforce MFA across the organization.
   - **Answer**: Enforcing MFA involves enabling MFA for all IAM users and roles using AWS IAM policies. Integrating MFA with AWS Single Sign-On (SSO) ensures consistent application. Regular audits and compliance checks ensure adherence, and training programs raise awareness among users.

5. **Reviewing and Updating IAM Policies**:
   - **Question**: A security audit identified vulnerabilities in the IAM policies. How would you review and update IAM policies to address these vulnerabilities?
   - **Answer**: Conducting a thorough review of IAM policies involves identifying overly permissive policies and refining them based on the principle of least privilege. Using AWS IAM Access Analyzer and AWS Config rules helps detect and remediate issues. Regular audits and automated compliance checks ensure policies remain secure and up-to-date.

These scenario-based questions reflect real-world challenges and require practical solutions, demonstrating your experience and expertise in handling complex environments. Good luck with your interviews!