# User-Behavior-Analytics-UBA-for-Insider-Threat-Detection
This repository contains an AI-driven User Behavior Analytics (UBA) system designed to detect insider threats by analyzing user activity patterns. The software leverages machine learning algorithms to monitor, identify, and flag anomalous behavior that may indicate potential security risks within an organization.

User Behavior Analytics for Insider Threat Detection
This project provides a tool for monitoring and analyzing user activities to identify suspicious patterns that might indicate potential insider threats.
Overview
Insider threats are one of the most challenging security problems for organizations. This tool uses machine learning to detect anomalous user behavior by analyzing various activities including login patterns, file access, after-hours activity, and sensitive data access.
Features

Data Processing: Import and preprocess user activity logs
Feature Extraction: Convert raw logs into behavioral indicators
Anomaly Detection: Identify unusual patterns using Isolation Forest algorithm
Alert Generation: Create actionable alerts for security teams
Visualization: Generate graphs to help visualize potential threats
Reporting: Export results to CSV and JSON formats

Installation

Clone the repository:
Copygit clone https://github.com/yourusername/insider-threat-detection.git
cd insider-threat-detection

Install the required dependencies:
Copypip install -r requirements.txt


Usage
Basic Usage
Run the main script:
pythonCopypython insider_threat_detection.py
This will:

Generate demo data if none exists
Process the data
Detect anomalies
Generate alerts
Create visualizations
Save all results to the "reports" directory

Custom Usage
You can also import the UserBehaviorAnalytics class and use it with your own data:
pythonCopyfrom insider_threat_detection import UserBehaviorAnalytics

# Initialize the analyzer
uba = UserBehaviorAnalytics(config_path="your_config.json")

# Run the analysis
results = uba.run_analysis("your_data.csv", "output_directory")

# Access the results
alerts = uba.alerts
Input Data Format
The system expects a CSV file with the following columns:

user_id: Unique identifier for each user
timestamp: Date and time of the activity
action: Type of action (login, logout, file_access, etc.)
resource: The resource being accessed

Example:
Copyuser_id,timestamp,action,resource
user_001,2023-05-01 08:55:23,login,system
user_001,2023-05-01 09:12:45,file_access,resource_05
user_001,2023-05-01 17:05:12,logout,system
Configuration
The system can be configured using a JSON file with the following structure:
jsonCopy{
  "anomaly_detection": {
    "contamination": 0.05,
    "n_estimators": 100,
    "random_state": 42
  },
  "alert_threshold": 0.8,
  "feature_weights": {
    "login_time_variance": 1.0,
    "file_access_count": 1.0,
    "after_hours_activity": 1.5,
    "failed_login_attempts": 2.0,
    "sensitive_data_access": 2.0
  },
  "working_hours": {
    "start": "09:00",
    "end": "17:00"
  }
}
Output
The system generates several output files in the specified output directory:

anomaly_detection_results.csv: Complete results with anomaly scores for all users
alerts.json: Detailed alerts for high-risk users
anomaly_scores.png: Visualization of anomaly scores
feature_distribution.png: Comparison of feature distributions between normal and anomalous users

Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
License
This project is licensed under the MIT License - see the LICENSE file for details.
