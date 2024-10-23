# LoRA-Inlaid

This is the anonymous repository for submitting paper **Efficient Multi-task LLM Quantization and Serving for Multiple LoRA Adapters**.

## Code Structure
The project's code base is organized in the following directory structure.

```shell
├── data
├── figures
├── lorainlaid
├── models
├── test
├── third_party
├── install.sh
├── LICENSE
└── README.md
```

## Installation

To use this repository, please follow the steps below to install the required dependencies.

### Prerequisites
- Python (version 3.10.13)
- pip (version 24.0)
- cuda (version 12.1)

### Install LoRA-Inlaid
1. Clone the repository

2. Install the modified gptq in third_party

3. Install LoRA-Inlaid

4. Install Acceleration lib for exllama

We have organized the installation process in `install.sh`, and users only need to `bash install.sh` to complete it
## Data and Model Preparation
Before we could run, we must prepare the models and datasets we need.

### Models
`models/download_model.py`: download the models we need.
`models/download_lora.py`: download the lora adapters we need.

Users can download all the models and lora adapters use the following commands:
```bash
cd models
bash download.sh
```
It should be noted that for llama models, users should use their own access_tokens.
### Datasets
`data/download_data.py`: download the datasets we need.
Users can download all the datasets use the following commands:
```bash
cd data
bash download.sh
```

## Quick Start
Once users have finished the Preparation for data and models, they can quikcly start use the following commands:
```bash
cd test/performance
bash launch_server_7b_lorainlaid.sh
```
After the server has been launched, run the following commands to send requests:
```bash
bash run_exp_test.sh
```

## Run test
To run the main tests in paper, please follow the steps below.

### Accuracy
We pack all test in one script, users should following the commands below:
```bash
cd test/accuracy
bash run_all_test.sh
```

### Performance
Performance tests include the test for Throughput, Latency, JCT and SLO.
```bash
# launch lorainlaid-7b
cd test/performance
bash launch_server_7b_lorainlaid.sh

# launch lorainlaid-13b
cd test/performance
bash launch_server_13b_lorainlaid.sh

# launch slora-7b
cd test/performance
bash launch_server_7b_slora.sh

# launch slora-13b
cd test/performance
bash launch_server_13b_slora.sh

# launch vllm-7b
cd test/performance
bash launch_server_7b_vllm-1.sh
bash launch_server_7b_vllm-2.sh
bash launch_server_7b_vllm-4.sh

# launch vllm-13b
cd test/performance
bash launch_server_13b_vllm-1.sh
bash launch_server_13b_vllm-2.sh
bash launch_server_13b_vllm-4.sh
```
Once you have launched one of these servers, you should send requests by:
```bash
bash run_exp.sh
```
