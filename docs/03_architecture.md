# 03 – System Architecture and Data Flow

## 1. Overview
This document describes the technical architecture of the **SecureDataChain ETL Project**, illustrating how data moves from raw sources through the ETL pipeline and is finally secured using a blockchain-based integrity layer.

---

## 2. System Components
| Component | Description | Technology |
|------------|-------------|-------------|
| **Raw Data Source** | Input logs, events, or datasets (synthetic or anonymized). | CSV, JSON, APIs |
| **ETL Pipeline** | Extracts, cleans, transforms, and loads data. | Python (pandas, hashlib) |
| **Hash Generator** | Creates a SHA-256 hash of the processed dataset. | Python hashlib |
| **Blockchain Layer** | Records dataset hashes for immutability and traceability. | Custom Python module |
| **Verification Module** | Validates dataset integrity by comparing stored and computed hashes. | Python CLI or script |

---

## 3. Data Flow Diagram

 +-------------------+
 |  Data Source(s)   |
 +---------+---------+
           |
           v
 +-------------------+
 |   ETL Pipeline    |
 | (Extract/Transform|
 |       /Load)      |
 +---------+---------+
           |
           v
 +-------------------+
 |  Hash Generator   |
 | (SHA-256 Digest)  |
 +---------+---------+
           |
           v
 +-------------------+
 |  Blockchain Layer |
 | (Record + Verify) |
 +---------+---------+
           |
           v
 +-------------------+
 |   Data Integrity  |
 |    Verification   |
 +-------------------+


---

## 4. Architecture Layers

1. **Data Layer** → contains raw and processed datasets (`/data/raw` and `/data/processed`).  
2. **Processing Layer** → handles ETL and data transformation logic (`src/etl_pipeline.py`).  
3. **Integrity Layer** → generates dataset hashes and records them in blockchain (`src/blockchain.py`).  
4. **Validation Layer** → verifies integrity and alerts if data has been altered.  

---

## 5. User runs the ETL pipeline on raw data:

 "python src/etl_pipeline.py"


