# Dataset

The raw dataset is **not** included in this repository because of its size (the CSV copy of the x86 PCAP file is about 124 MB), and we have not checked its redistribution terms.

## Dataset used

**CIC-YNU-IoTMal Dataset 2026**, prepared by the Canadian Institute for Cybersecurity (University of New Brunswick) with Yokohama National University.
We used only the **x86 PCAP** (network-traffic) file.

Official dataset page: https://www.unb.ca/cic/datasets/ynu-iot-2026.html
Please get the data from that page and follow its terms and citation instructions.

## Where to place it

Our notebook was run in Google Colab and loads the file with:

```python
from google.colab import files
uploaded = files.upload()          # we uploaded pcap.parquet
df = pd.read_parquet("pcap.parquet")
```

To run it locally, put the file in this folder (`data/`) and change the path in the loading cell, for example `pd.read_parquet("data/pcap.parquet")`.

## What our copy looked like

| Item | Value |
|---|---|
| Raw shape | 455,641 rows, 42 columns |
| After removing `Unknown` labels | 424,110 rows |
| After dropping `Hash` and `Arch` | 424,110 rows, 40 columns (39 features + `MalwareFamily`) |

Classes used: Benign, DarkNexus, Gafgyt, Generic, Mirai.
