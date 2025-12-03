
Flow Reconstruction Using Payload-Byte

This repository contains an extended version of the Payload-Byte labeling pipeline, modified to additionally reconstruct flows and packet-level ordering from PCAP files.
The aim of this project is to take raw network traffic, generate packet-level labels, and enrich them with metadata required for downstream flow-based analysis.


README.md
Flow Reconstruction Extension for Payload-Byte

This repository extends the original Payload-Byte pipeline by adding flow reconstruction and packet ordering to the packet-level labeled dataset generated from raw PCAP files.

The notebook flow_reconstruction.ipynb demonstrates how to:

Re-run the Payload-Byte labeling pipeline

Reconstruct flows using a 5-tuple

Assign a unique flow_id

Compute chronological packet_order within each flow

Export an enriched packet-level labeled dataset

Features

✔ Packet-level labeling (via Payload-Byte pipeline)

✔ Flow reconstruction

✔ Packet ordering per flow

✔ Output compatible with ML models requiring sequence-aware data

✔ Fully reproducible from original PCAP files

Project Layout
.
├── flow_reconstruction.ipynb      # Main notebook
├── pipeline/                      # Modified/extended Payload-Byte code
├── data/                          # Input PCAPs and output CSVs
├── requirements.txt
└── README.md


(Rename folders according to your final structure.)

Setup
1. Install Dependencies
pip install -r requirements.txt

2. Place Input Data

Place your raw PCAP files and label CSVs inside:

data/
    pcap/
    labels/

Usage
Run Through the Notebook

Open:

flow_reconstruction.ipynb


Then run all cells to:

Generate packet-level labels

Compute flow identifiers

Assign packet order

Export:

data/packet_level_with_flows.csv

Output Schema
Column	Description
timestamp	Packet timestamp
src_ip	Source IP address
dst_ip	Destination IP address
src_port	Source port
dst_port	Destination port
protocol	IP protocol
flow_id	Unique identifier for each flow
packet_order	Position of packet inside its flow
label	Packet label (benign / attack type)
payload_bytes	Extracted payload data
Acknowledgement

This work builds upon the original open-source project Payload-Byte by
Yasir Ali Farrukh and contributors.
