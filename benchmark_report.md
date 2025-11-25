# PQC RTL Implementation Benchmark Results

This report contains automated benchmark results for open-source PQC hardware implementations.

---

## DILITHIUM

| Implementation | Type | Platform | LUTs | FFs | BRAMs | DSPs | Status |
|:---|:---|:---|---:|---:|---:|---:|:---|
| [gmucerg-dilithium](https://github.com/GMUCERG/Dilithium) | full_accelerator | fpga | N/A | N/A | N/A | 32 | complete |

### gmucerg-dilithium

**Repository**: https://github.com/GMUCERG/Dilithium

**Type**: full_accelerator

**Language**: vhdl

**Security Levels**: 2, 3, 5

**SCA Protected**: False

**Notes**: Full implementation with NTT-2x2 architecture

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 32

**Simulation Results**:

- Cycles: 11040
- Latency: 107.088 µs

---

## KYBER

| Implementation | Type | Platform | LUTs | FFs | BRAMs | DSPs | Status |
|:---|:---|:---|---:|---:|---:|---:|:---|
| [xingyf14-kyber](https://github.com/xingyf14/CRYSTALS-Kyber) | full_accelerator | fpga | N/A | N/A | N/A | 24 | complete |
| [bsc-loca-kyber-hls](https://github.com/bsc-loca/PQC-Crystals-HLS-Accelerators) | full_accelerator | fpga | N/A | N/A | N/A | 48 | complete |

### xingyf14-kyber

**Repository**: https://github.com/xingyf14/CRYSTALS-Kyber

**Type**: full_accelerator

**Language**: verilog

**Security Levels**: 512, 768, 1024

**SCA Protected**: False

**Notes**: Full accelerator implementation for Kyber

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 24

**Simulation Results**:

- Cycles: 4350
- Latency: 41.325 µs

---

### bsc-loca-kyber-hls

**Repository**: https://github.com/bsc-loca/PQC-Crystals-HLS-Accelerators

**Type**: full_accelerator

**Language**: hls

**Security Levels**: 512, 768, 1024

**SCA Protected**: False

**Notes**: HLS-based unified accelerator for Kyber and Dilithium

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 48

**Simulation Results**:

- Cycles: 2980
- Latency: 29.204 µs

---

## MCELIECE

| Implementation | Type | Platform | LUTs | FFs | BRAMs | DSPs | Status |
|:---|:---|:---|---:|---:|---:|---:|:---|
| [pmassolino-mceliece](https://github.com/pmassolino/hw-goppa-mceliece) | full_accelerator | fpga | N/A | N/A | N/A | 8 | complete |

### pmassolino-mceliece

**Repository**: https://github.com/pmassolino/hw-goppa-mceliece

**Type**: full_accelerator

**Language**: vhdl

**Security Levels**: 3488, 6688

**SCA Protected**: True

**Notes**: Binary Goppa codes implementation with constant-time solving

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 8

**Simulation Results**:

- Cycles: 152000
- Latency: 1596.0 µs

---

## NTRU

| Implementation | Type | Platform | LUTs | FFs | BRAMs | DSPs | Status |
|:---|:---|:---|---:|---:|---:|---:|:---|
| [adrianmarotzke-sntrup](https://github.com/AdrianMarotzke/SNTRUP_on_FPGA) | full_accelerator | fpga | N/A | N/A | N/A | 31 | complete |

### adrianmarotzke-sntrup

**Repository**: https://github.com/AdrianMarotzke/SNTRUP_on_FPGA

**Type**: full_accelerator

**Language**: vhdl

**Security Levels**: 761

**SCA Protected**: True

**Notes**: Constant-time implementation of Streamlined NTRU Prime

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 31

**Simulation Results**:

- Cycles: 64026
- Latency: 224.091 µs

---

## SABER

| Implementation | Type | Platform | LUTs | FFs | BRAMs | DSPs | Status |
|:---|:---|:---|---:|---:|---:|---:|:---|
| [sujoyetc-saber](https://github.com/sujoyetc/SABER_HW) | full_accelerator | fpga | N/A | N/A | N/A | 0 | complete |

### sujoyetc-saber

**Repository**: https://github.com/sujoyetc/SABER_HW

**Type**: full_accelerator

**Language**: vhdl

**Security Levels**: 3

**SCA Protected**: False

**Notes**: Instruction set coprocessor architecture

**Synthesis Results**:

- LUTs: N/A
- Flip-Flops: N/A
- BRAMs: N/A
- DSPs: 0

**Simulation Results**:

- Cycles: 6618
- Latency: 26.472 µs

---

## Summary Statistics

- Total implementations: 6
- Complete benchmarks: 6
- Synthesis only: 0
- Failed: 0

