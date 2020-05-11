# Overview

This repository contains measurement data of VM startup time from [AWS](https://aws.amazon.com) and [Google Cloud](https://cloud.google.com/).
* **Data Release Date: May, 2020**
* Measurement Period: Jan. 2020 - Mar. 2020.
* VM types
  | Provider | VM Type        | # CPU | Memory | On-demand Price | Note |
  | ---      | ---            | ---   | ---    | ---             | ---  |
  | AWS      | t2.nano        | 1     | 0.5    | $0.0058/Hr      |      |
  | AWS      | t2.micro       | 1     | 1.0    | $0.0116/Hr      |      |
  | AWS      | t2.small       | 1     | 2.0    | $0.023/Hr       |      |
  | AWS      | t2.medium      | 2     | 4.0    | $0.0464/Hr      |      |
  | AWS      | t3.nano        | 2     | 0.5    | $0.0052/Hr      |      |
  | AWS      | t3.micro       | 2     | 1.0    | $0.0104/Hr      |      |
  | AWS      | t3.small       | 2     | 2.0    | $0.0208/Hr      |      |
  | AWS      | t3a.medium     | 2     | 4.0    | $0.0376/Hr      | AMD EPYC 7000 |
  | AWS      | m4.large       | 2     | 8.0    | $0.10/Hr        |      |
  | AWS      | m4.xlarge      | 4     | 16.0   | $0.20/Hr        |      |
  | AWS      | m5a.large      | 2     | 8.0    | $0.086/Hr       | AMD EPYC 7000 (with 2.5GHz) |
  | AWS      | m5.xlarge      | 4     | 16.0   | $0.192/Hr       |      |
  | Google   | f1-micro       | 1     | 0.6    | $0.007/Hr       |      |
  | Google   | g1-small       | 1     | 1.7    | $0.021/Hr       |      |
  | Google   | n1-standard-1  | 1     | 3.75   | $0.038/Hr       |      |
  | Google   | n1-standard-2  | 2     | 7.5    | $0.076/Hr       |      |
  | Google   | n1-standard-4  | 4     | 15.0   | $0.15/Hr        |      |
  | Google   | n2-standard-2  | 2     | 8.0    | $0.078/Hr       | Xeon (Cascade Lake) |
  | Google   | n2-standard-4  | 4     | 16.0   | $0.156/Hr       | Xeon (Cascade Lake) |
  | Google   | n2d-standard-2 | 2     | 8.0    | $0.068/Hr       | AMD EPYC Rome |
  | Google   | n2d-standard-4 | 4     | 16.0   | $0.136/Hr       | AMD EPYC Rome |
  | Google   | e2-standard-2  | 2     | 8.0    | $0.068/Hr       | Either Intel or AMD |
  | Google   | e2-standard-4  | 4     | 16.0   | $0.135/Hr       | Either Intel or AMD |
  
* OS types: Linux (Ubuntu 18.04 LTS), Windows (Server 2016)
* Data Centers/Regions
  | Provider | Region         | Availability Zones | Location              |
  | ---      | ---            | ---                | ---                   |
  | AWS      | us-east-1      | a, b, c, d, f      | Northern Virginia     |
  | AWS      | us-west-3      | a, b, c            | Oregon                |
  | AWS      | eu-west-3      | a, b, c            | Paris, France         |
  | AWS      | ap-southeast-1 | a, b, c            | Singapore             |
  | Google   | us-east4       | a, b, c            | Northern Virginia     |
  | Google   | us-west1       | a, b, c            | The Dalles, Oregon    |
  | Google   | europe-west1   | b, c, d            | St. Ghislain, Belgium |
  | Google   | asia-southeast1| a, b, c            | Singapore             |

* Base Image Size: 32GB, 64GB, 128GB, 256GB
* VM purchase models
  - AWS: On-demand vs. [Spot](https://aws.amazon.com/ec2/spot/)
  - Google Cloud: On-demand vs. [Preemptible](https://cloud.google.com/preemptible-vms)

# Dataset File Schema
* Each csv file (dataset) contains VM startup time measurement results for a specific VM type (file name == VM type)
  - e.g., `t2-nano.csv`: VM startup time measurement results for t2.nano type in AWS
* Each dataset contains the following fields:
  - **VM Type**: the name of VM type. e.g., t2.nano
  - **Provider**: AWS or Google
  - **Region**: AWS region or Google cloud region
  - **Zone**: (Availability) Zone in a Region
  - **Purchase Model**: O: On-demand, S: Spot (AWS), P: Preemptible (Google)
  - **OS**: Linux (Ubuntu 18.04 LTS) or Windows (Server 2016)
  - **Image Size**: Integer, 32GB - 256GB
  - **Startup Type**: Cold or Warm
  - **Measurement Datatime**: Measurement date and time (based on local time)
  - **Startup Time**: Startup Time (Second)
  
