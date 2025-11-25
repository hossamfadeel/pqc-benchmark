# PQC RTL Benchmarking Framework

This repository provides an automated framework for benchmarking open-source hardware (RTL) implementations of post-quantum cryptography (PQC) algorithms. It is designed to clone, build, simulate, and analyze various PQC implementations to provide a standardized comparison of their performance and resource utilization.

## Features

- **Automated Benchmarking**: Scripts to automatically clone, synthesize, and simulate PQC implementations.
- **Multi-Algorithm Support**: Supports Kyber, Dilithium, Saber, NTRU, Falcon, Classic McEliece, and SPHINCS+.
- **Performance & Resource Extraction**: Automatically parses tool reports to extract key metrics (LUTs, FFs, BRAMs, DSPs, latency, frequency).
- **Standardized Reporting**: Generates unified Markdown and CSV reports for easy comparison.
- **Modular Design**: Easily extendable to include new algorithms and implementations via a simple YAML configuration.
- **Open-Source Toolchain**: Primarily uses open-source simulators like Icarus Verilog and GHDL for simulation-based benchmarks.

## Repository Structure

```
/pqc-benchmark
├── algorithms/         # Cloned PQC implementation repositories
│   ├── kyber/
│   └── dilithium/
├── configs/
│   └── implementations.yaml # Main configuration file for all implementations
├── docs/                 # Detailed documentation
│   └── CONTRIBUTING.md
├── results/              # Generated benchmark reports and charts
│   ├── benchmark_report.md
│   ├── benchmark_results.csv
│   └── kyber_resource_comparison.png
├── scripts/              # Main automation scripts
│   ├── benchmark.py      # Main benchmarking orchestrator
│   └── report_generator.py # Report generation module
├── tools/                # Helper scripts and templates
│   ├── parse_vivado_reports.py
│   └── vivado_synth_template.tcl
├── Makefile              # Makefile for easy command access
├── README.md             # This file
└── requirements.txt      # Python dependencies
```

## Quick Start

### 1. Prerequisites

- **Python 3.8+** and `pip`
- **Git**
- **FPGA Synthesis Tools** (Optional, for synthesis benchmarks):
  - Xilinx Vivado
- **RTL Simulators** (Optional, for simulation benchmarks):
  - Icarus Verilog (`iverilog`)
  - GHDL

### 2. Installation

Clone this repository and install the required Python dependencies:

```bash
git clone <this-repo-url> pqc-benchmark
cd pqc-benchmark
pip3 install -r requirements.txt
```

### 3. Running Benchmarks

You can use the provided `Makefile` to run the benchmarks.

**Clone all repositories:**

```bash
make clone
```

**Run the full benchmark suite (clone, synthesize, simulate):**

```bash
make benchmark
```

**Run benchmarks for a specific algorithm:**

```bash
make benchmark-kyber
make benchmark-dilithium
```

After the benchmarks are complete, the results will be available in the `results/` directory.

## How to Add a New Implementation

Adding a new PQC implementation to the benchmark framework is straightforward:

1.  **Open the Configuration File**: Edit `configs/implementations.yaml`.

2.  **Add a New Entry**: Under the appropriate algorithm (e.g., `kyber`), add a new entry for your implementation. Follow the existing structure:

    ```yaml
    kyber:
      - name: my-new-kyber-impl
        repo: https://github.com/user/my-new-kyber-impl
        type: full_accelerator
        platform: fpga
        target_device: artix7
        language: verilog
        security_levels: [768]
        sca_protected: false
        build_system: vivado
        notes: "My new awesome Kyber implementation."
    ```

3.  **Run the Benchmark**: The framework will automatically pick up the new implementation the next time you run `make benchmark` or `make benchmark-kyber`.

For more details, see `docs/CONTRIBUTING.md`.

## Output Format

The benchmark results are generated in multiple formats in the `results/` directory:

-   **`benchmark_report.md`**: A detailed Markdown report with tables and summaries for each algorithm.
-   **`benchmark_results.csv`**: A CSV file containing all raw data, suitable for analysis in spreadsheet software or pandas.
-   **`*.png`**: Comparison charts visualizing resource utilization for each algorithm.

### Example CSV Columns

| algorithm | name | repo | type | platform | language | luts | ffs | brams | dsps | max_frequency_mhz | cycles | latency_us | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## Disclaimer

This framework is a prototype and relies on the structure of the target repositories. Synthesis and simulation may fail if the target repositories have non-standard project structures or require specific tool versions. The provided scripts are intended as a starting point and may require modification to work with all implementations.
