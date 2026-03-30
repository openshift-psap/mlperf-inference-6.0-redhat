# MLPerf Inference Benchmark Results

This repository contains our MLPerf Inference v6.0 benchmark results and setup documentation.

## Results Summary

### NVIDIA Hardware Results

| Model Category | Model | GPU Configuration | Offline Scenario (throughput) | Server Scenario (throughput) | Software Stack |
|---------------|-------|-------------------|-------------------------------|------------------------------|----------------|
| **Vision Model** | Qwen3-VL-235B-A22B | 8x H200 | 18.02 samples/sec | 11.05 samples/sec | RHEL, vLLM |
| | | 8x B200 | 79.04 samples/sec | 67.86 samples/sec | RHEL, vLLM |
| **Reasoning Model** | gpt-oss-120b | 8x H200 | 28,680 tokens/sec | 24,103.19 tokens/sec | OpenShift, llm-d, vLLM |
| | | 8x B200 (180 GB) | 93,070.70 tokens/sec | 71,588.13 tokens/sec | OpenShift, llm-d, vLLM |
| **Speech2Text** | Whisper | 2x L40S | 3,646.91 tokens/sec | N/A | RHEL, vLLM |
| | | 8x H200 | 36,395.70 tokens/sec | N/A | RHEL, vLLM |

### AMD Hardware Results

| Model Category | Model | GPU Configuration | Offline Scenario (throughput) | Server Scenario (throughput) | Software Stack |
|---------------|-------|-------------------|-------------------------------|------------------------------|----------------|
| **Dense Model** | llama-2-70b | 8x MI350x (with SMC) | 91,933.10 tokens/sec | 89,019.65 tokens/sec | vLLM, RHEL, AMD |
| **Reasoning Model** | gpt-oss-120b | 8x MI350x (with SMC) | 64,293.30 tokens/sec | 58,373.27 tokens/sec | vLLM, RHEL, AMD |

## Submission Results

For detailed submission results, see: [MLCommons Inference Results](https://mlcommons.org/benchmarks/inference/) <!-- Update with actual submission link -->

## Setup Documentation

Detailed setup and configuration instructions for each benchmark:

- **GPT-OSS-120B**: See [harness/README.md](mlperf-inference-6.0-redhat/harness/README.md) for harness setup and configuration
- **Whisper**: See [speech2text/Whisper_Setup.md](mlperf-inference-6.0-redhat/speech2text/Whisper_Setup.md) for setup instructions
- **Qwen3-VL**: See [multimodal/qwen3-vl/README.md](mlperf-inference-6.0-redhat/multimodal/qwen3-vl/README.md) for setup instructions

## Repository Structure

```
.
├── README.md (this file)
└── mlperf-inference-6.0-redhat/
    ├── harness/              # GPT-OSS-120B harness and configuration
    ├── speech2text/          # Whisper benchmark setup
    ├── multimodal/           # Qwen3-VL vision model setup
    └── language/             # Language model benchmarks
```

## About MLPerf Inference

MLPerf Inference is a benchmark suite for measuring how fast systems can run models in a variety of deployment scenarios. For more information, visit [MLCommons](https://mlcommons.org/).

## Scenarios

- **Offline**: Batch inference maximizing throughput
- **Server**: Online serving under TTFT (Time To First Token) and TPOT (Time Per Output Token) constraints
