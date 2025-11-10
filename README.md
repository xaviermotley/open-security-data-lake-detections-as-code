# 🧠 Open Security Data Lake + Detections‑as‑Code  
**OCSF + Sigma + Attack Simulation on AWS**  

## 📘 Overview  
This project demonstrates how to **build a modern, open security data lake** and **operationalize detections‑as‑code (DaC)** using AWS services, OCSF normalization, and CI/CD pipelines for Sigma-based analytics.  
The lab combines the **AWS re:Inforce 2025 Security Lake workshop** with **community‑driven DaC pipelines**, **Sigma rule authoring**, and **attack simulations via Stratus Red Team**—showcasing how to go from *data collection → detection → validation* in a single automated workflow.  

## 🏗️ Architecture  
```mermaid  
graph TD  
    A[Collect Security Logs from AWS Services] --> B[Amazon Security Lake (OCSF Format)]  
    B --> C[Query and Analyze Data via Athena / Jupyter Notebooks]  
    C --> D[Detections-as-Code Pipeline (Sigma + CI/CD)]  
    D --> E[Rule Compilation & Version Control in GitHub]  
    E --> F[Deploy Rules to SIEM / SOAR (Splunk, Sentinel, etc.)]  
    F --> G[Attack Simulation via Stratus Red Team]  
    G --> H[Validate Detection Coverage and Generate Reports]  
```  

## 🔧 Components  
### **1. Open Security Data Lake (OCSF on AWS)**  
Based on *“AWS re:Inforce 2025 – Operationalizing Amazon Security Lake (hands‑on)”*  
- Builds and configures **Amazon Security Lake**  
- Ingests multi‑account and multi‑region telemetry  
- Normalizes events using **OCSF schema**  
- Queries events with **Athena** or **Jupyter notebooks**  
📂 Folder: `infrastructure/`  
Includes AWS CDK or Terraform templates to provision Security Lake resources.  

### **2. Detections‑as‑Code (DaC)**  
Inspired by *“From Soup to Nuts: Building a Detection‑as‑Code Pipeline”*  
- **Version‑controlled Sigma rules** stored in `/detections/`  
- **CI/CD pipeline** automatically tests, compiles, and validates rules  
- Ensures **consistent quality**, **unit tests**, and **artifact promotion**  
📂 Folder: `detections/`  
Includes YAML Sigma rules + CI pipeline for validation and build automation.  

### **3. Sigma Rule Authoring + Validation**  
Based on *“How to Level Up Your SOC Skill with Sigma”*  
- Write and compile Sigma rules into target query languages (e.g., SPL, KQL)  
- Validate syntax, mapping, and coverage via unit tests  
- Integrate compiled detections into your SIEM of choice  
📂 Folder: `sigma/`  
Contains rule templates, mappings, and conversion scripts.  

### **4. Attack Simulation (Stratus Red Team)**  
Based on *“Reproducing Common Attacks in the Cloud with Stratus Red Team”*  
- Simulates AWS‑native attack techniques (e.g., IAM privilege escalation, data exfiltration)  
- Validates detections in real time against Security Lake + DaC pipeline  
- Enables continuous purple‑team validation  
📂 Folder: `tests/`  
Includes Stratus Red Team YAML scenarios and validation outputs.  

## 🧩 Putting It All Together  
| Stage | Tooling | Purpose |  
|-------|---------|---------|  
| **Data Collection** | Amazon Security Lake | Centralize & normalize logs |  
| **Schema** | OCSF | Standardize telemetry format |  
| **Detection Authoring** | Sigma | Create portable rules |  
| **Automation** | GitHub Actions / CI | Test and compile detections |  
| **Validation** | Stratus Red Team | Simulate attacks & verify coverage |  

## 🚀 Getting Started  
1. **Provision Security Lake**  
   - Clone this repo  
   - Deploy infrastructure under `/infrastructure` using CDK or Terraform  
   - Enable sources (CloudTrail, GuardDuty, VPC Flow Logs, etc.)  
2. **Deploy the Detection Pipeline**  
   - Push or modify Sigma rules under `/detections`  
   - CI/CD automatically compiles, validates, and publishes results  
3. **Run Attack Simulations**  
   - Install [Stratus Red Team](https://stratus-red-team.cloud/)  
   - Execute test scenarios from `/tests`  
   - Review detection hits and coverage reports  

## 📊 Example Output  
```bash  
$ stratus run aws.iam.enumerate_roles  
$ pytest tests/  
All detections validated successfully!  
```  

## 🧩 Future Enhancements  
- Integrate with **AWS Glue + Bedrock for AI‑driven detection enrichment**  
- Build coverage dashboards mapping to **MITRE ATT&CK**  
- Add **SOAR integrations** for auto‑response workflows  

## 🧑‍💻 Credits & References  
- [AWS re:Inforce 2025 – Operationalizing Amazon Security Lake (hands‑on)](https://reinforce.awsevents.com/)  
- [From Soup to Nuts: Building a Detection‑as‑Code Pipeline](https://www.youtube.com/)  
- [Sigma Project](https://github.com/SigmaHQ/sigma)  
- [Stratus Red Team](https://github.com/DataDog/stratus-red-team)  
- [OCSF](https://github.com/ocsf/ocsf-schema)
