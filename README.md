# Network Intrusion Detection Evaluation 

[Project Notebook](https://github.com/SMozaffar/Network-intrusion-analysis/blob/main/network-analysis.ipynb)

## Project Overview

This project involves the analysis and evaluation of a Network Intrusion Detection System (NIDS) using the NSL-KDD dataset. The NSL-KDD dataset is an improved version of the original KDD Cup 1999 dataset, designed to evaluate the performance of NIDS. The main goal of this project is to apply various machine learning models to classify network traffic as either normal or one of several types of attacks. The models evaluated in this project include:

- **Gaussian Naive Bayes**
- **Random Forest**
- **Multi-layer Perceptron (MLP)**
- **Support Vector Machine (SVM)**
- **Decision Tree**

## Dataset Overview

The NSL-KDD dataset consists of 41 features extracted from network traffic data, along with a label that indicates whether the connection was normal or an attack. The dataset is structured to include a wide range of attack types that represent various forms of malicious activity.

### Key Features

Some of the features in the dataset include:

- **duration**: Length (in seconds) of the connection.
- **protocol_type**: Type of protocol (e.g., TCP, UDP, ICMP).
- **service**: Network service on the destination (e.g., HTTP, FTP, SMTP).
- **src_bytes**: Number of data bytes sent from source to destination.
- **dst_bytes**: Number of data bytes sent from destination to source.
- **flag**: Normal or error status of the connection.
- **count**: Number of connections to the same host as the current connection in the past two seconds.
- **srv_count**: Number of connections to the same service as the current connection in the past two seconds.
- **label**: Indicates whether the connection is normal or an attack, along with the specific type of attack.

### Class Labels and Their Meanings

The `label` in the dataset identifies whether a connection is "normal" or an attack. If it is an attack, the label also specifies the type of attack. Below is an explanation of each unique class label:

- **normal**: Represents regular, non-malicious network traffic.
- **neptune**: A type of Denial of Service (DoS) attack where many SYN packets are sent to a target, overwhelming it.
- **back**: Another DoS attack, which floods a server with spoofed requests, causing it to become unresponsive.
- **land**: A DoS attack where a network packet is sent with the same source and destination IP address and port number, causing the target to crash or freeze.
- **pod (Ping of Death)**: A DoS attack that sends malformed or oversized packets, leading to crashes.
- **smurf**: A DoS attack involving a network packet sent to a large number of devices that reply to the spoofed IP address of the target, overwhelming it with traffic.
- **teardrop**: A DoS attack where fragmented packets are sent to a machine, causing it to crash due to the inability to reassemble the fragments.
- **warezclient**: An unauthorized file transfer attack, where a malicious client downloads files from a compromised server.
- **warezmaster**: Similar to `warezclient`, but the attack involves uploading unauthorized files to a server.
- **ftp_write**: An attack where a malicious actor writes files to an FTP server, potentially causing harm.
- **guess_passwd**: A brute-force attack aimed at guessing a user's password.
- **imap**: An attack on the IMAP email protocol, usually involving unauthorized access.
- **phf**: A web-based attack exploiting a vulnerability in older web servers to execute malicious commands.
- **portsweep**: A reconnaissance attack where the attacker scans a range of ports on a target machine to identify open services.
- **satan**: A network scanning attack where the attacker probes systems for known vulnerabilities.
- **nmap**: A network mapping attack where the attacker scans a network to identify live hosts and open ports.
- **rootkit**: A type of attack where the attacker installs a rootkit, gaining unauthorized root access to a system.
- **buffer_overflow**: An attack that exploits a buffer overflow vulnerability, potentially allowing the attacker to execute arbitrary code.
- **loadmodule**: An attack where malicious modules are loaded into the kernel, compromising the system.
- **perl**: A type of remote-to-local attack where the attacker uses a Perl script to exploit a vulnerability on the target machine.
- **spy**: An attack involving eavesdropping or capturing sensitive data from a victim's system.
- **multihop**: An attack where an intruder uses multiple hops to access a target, often to obscure the origin of the attack.

### Project Steps

1. **Data Loading and Preparation**: The NSL-KDD dataset is loaded, and irrelevant columns are removed. The dataset is then preprocessed, converting categorical features into numerical representations using one-hot encoding.

2. **Exploratory Data Analysis (EDA)**: Visualizations are created to understand the distribution of classes and key features. This includes a class distribution plot and histograms of select features.

3. **Data Cleaning**: The data is cleaned by handling missing values, converting data types, and ensuring the dataset is ready for model training.

4. **Feature Correlation Analysis**: A correlation matrix is computed and visualized to understand the relationships between different features.

5. **Model Evaluation**: Multiple machine learning models are trained and evaluated. Accuracy, precision, recall, and F1-score are computed for each model, and their performances are compared.

6. **Visualization**: The results are visualized, including a decision tree plot. A summary of the model performances is provided, along with insights drawn from the analysis.

### Model Performance Summary

The models were evaluated using various metrics, including accuracy, precision, recall, and F1-score. Below is a summary of the model performances:

| Model          | Accuracy | Precision (Macro Avg) | Recall (Macro Avg) | F1-Score (Macro Avg) |
|----------------|----------|-----------------------|--------------------|----------------------|
| GaussianNB     | 0.6254   | 0.3333                | 0.4023             | 0.3321               |
| RandomForest   | 0.9809   | 0.6926                | 0.6269             | 0.6369               |
| MLP            | 0.8961   | 0.4718                | 0.4374             | 0.4372               |
| SVM            | 0.4567   | 0.0535                | 0.0500             | 0.0425               |
| DecisionTree   | 0.9752   | 0.6241                | 0.6478             | 0.6244               |

## Discussion

This project demonstrates the application of machine learning models to classify network traffic into normal or attack categories using the NSL-KDD dataset. Ensemble methods like Random Forest are particularly effective for this type of task, offering both high accuracy and balanced performance across multiple metrics. Decision Trees also perform well, providing insight into how the model makes its decisions. Models like SVM may struggle with this dataset, indicating the importance of model selection and tuning in the context of NIDS. Additionally, feature importance analysis shows that network traffic metrics such as the number of bytes sent and connection status flags are crucial for detecting intrusions.

