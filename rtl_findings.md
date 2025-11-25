# RTL Implementation Research Findings

## CRYSTALS-Kyber Implementations

### 1. xingyf14/CRYSTALS-Kyber
- **Repository**: https://github.com/xingyf14/CRYSTALS-Kyber
- **Language**: VHDL (88.9%), Verilog (8.0%)
- **Platform**: FPGA (Xilinx Artix-7)
- **Type**: Full standalone hardware accelerator (server/client)
- **License**: Academic use only (stated in README)
- **Performance**:
  - Kyber-512: 3768 (keygen) / 5079 (encaps) / 6668 (decaps) cycles
  - Kyber-768: 6316 / 7925 / 10049 cycles
  - Kyber-1024: 9380 / 11321 / 13908 cycles
- **Resources** (server/client):
  - LUTs: 7412/6785
  - FFs: 4644/3981
  - Slices: 2126/1899
  - DSPs: 2/2
  - BRAMs: 3/3
  - Critical path: 6.2/6.0 ns
- **Security**: CCA-secure, verified against NIST KAT files
- **Side-channel countermeasures**: Not mentioned
- **Paper**: Published in TCHES (https://tches.iacr.org/index.php/TCHES/article/view/8797/8397)
- **Notes**: Includes NTT scheduling, Encode/Decode, Fujisaki-Okamoto transform

---


### 2. acmert/kyber-polmul-hw
- **Repository**: https://github.com/acmert/kyber-polmul-hw
- **Type**: Polynomial multiplication accelerator for Kyber
- **Notes**: Academic research only

### 3. bsc-loca/PQC-Crystals-HLS-Accelerators
- **Repository**: https://github.com/bsc-loca/PQC-Crystals-HLS-Accelerators
- **Language**: C++ (59.9%), VHDL (39.1%) - HLS-based
- **Platform**: FPGA-based SoCs (AMD Virtex UltraScale+ VCU118)
- **Type**: Full accelerator for both ML-KEM and ML-DSA
- **License**: Solderpad Hardware License v0.51
- **Tools**: Xilinx Vivado 2020.2, Vitis HLS 2021.2
- **Integration**: SELENE RISC-V SoC platform
- **Notes**: Unified accelerator supporting both Kyber and Dilithium with AXI interface

---

## CRYSTALS-Dilithium Implementations

### 1. GMUCERG/Dilithium
- **Repository**: https://github.com/GMUCERG/Dilithium
- **Language**: Verilog (65.7%), VHDL (18.2%), C++ (12.5%)
- **Platform**: FPGA
- **Type**: Full implementation (Keygen, Sign, Verify)
- **License**: Not explicitly stated
- **Security levels**: 2, 3, 5
- **Verification**: Verified against 100 NIST KATs
- **Features**: NTT-2x2 architecture
- **Maintainer**: CERG GMU (Luke Beckwith, Duc Nguyen, Kris Gaj)
- **Paper**: FPT'21 conference, available on ePrint and IEEE
- **Side-channel countermeasures**: Not mentioned
- **Notes**: High-performance design with combined top module

### 2. yathin017/CRYSTALS-Dilithium
- **Repository**: https://github.com/yathin017/CRYSTALS-Dilithium
- **Type**: High-performance FPGA implementation in Verilog
- **Notes**: Contains top module for full implementation

### 3. CALAS-CityU/SW-HW-Co-design-of-Dilithium
- **Repository**: https://github.com/CALAS-CityU/SW-HW-Co-design-of-Dilithium
- **Platform**: Xilinx Zynq architecture
- **Type**: Software/hardware co-design evaluation

---

## Classic McEliece Implementations

### 1. pmassolino/hw-goppa-mceliece
- **Repository**: https://github.com/pmassolino/hw-goppa-mceliece
- **Language**: VHDL (100%)
- **Platform**: FPGA
- **Type**: Full implementation (encryption/decryption) for binary (QD-)Goppa codes
- **License**: Has LICENSE.md file
- **Features**: 
  - Syndrome computation
  - Berlekamp-Massey algorithm
  - Polynomial evaluation for root search
  - Constant-time solving key equation
- **Maintainer**: Pedro Maat C. Massolino
- **Paper**: Master thesis (2014), ACM TECS 2015
- **Side-channel countermeasures**: Constant-time implementation mentioned
- **Notes**: Includes comprehensive testbenches, finite field arithmetic units (GF(2^m) for m=1 to 20)

### 2. Complete FPGA Implementation (Chen et al.)
- **Paper**: "Complete and Improved FPGA Implementation of Classic McEliece" (NIST PQC 2022)
- **Authors**: P.-J. Chen, T. T. H. Chen, B.-Y. Yang
- **Type**: First specification-compliant constant-time FPGA implementation
- **Features**: Pipelined Berlekamp-Massey, parallel syndrome computation

---


## SPHINCS+ Implementations

### 1. FPGA-based SPHINCS+ (Amiet et al.)
- **Paper**: "FPGA-based SPHINCS+ Implementations: Mind the Glitch" (2020)
- **Authors**: D. Amiet et al.
- **Type**: First efficient hardware implementation for SPHINCS+
- **Platform**: FPGA
- **Features**: Performance-optimized architecture, fault attack considerations
- **Notes**: Systematic approach to FPGA implementation

### 2. slh-dsa/sloth
- **Repository**: https://github.com/slh-dsa/sloth
- **Type**: SLotH accelerator for SLH-DSA (SPHINCS+)
- **Language**: C core implementation
- **Paper**: "Accelerating SLH-DSA by Two Orders of Magnitude" (NIST PQC 2024)
- **Features**: Hardware acceleration techniques for FIPS 205 SLH-DSA
- **Notes**: Focuses on efficient and secure hardware implementation

---

## FALCON Implementations

### 1. Hardware Implementation (Schmid et al.)
- **Paper**: "A Hardware Implementation of the Falcon Signature Scheme" (2023)
- **Authors**: M. Schmid et al.
- **Type**: First hardware implementation for Falcon signing and key generation
- **Citation count**: 23+
- **Notes**: Addresses challenges of floating-point FFT in hardware

### 2. vic9112/PQC_Falcon
- **Repository**: https://github.com/vic9112/PQC_Falcon
- **Type**: FPGA Implementation using High-Level Synthesis
- **Platform**: FPGA
- **Notes**: Hardware acceleration for Falcon digital signature

### 3. FalconSign (Ouyang et al.)
- **Paper**: Published in TCHES
- **Type**: High-performance, configurable crypto-processor
- **Platform**: FPGA/ASIC
- **Performance**: 5.1x speedup
- **Citation count**: 10+
- **Features**: Accelerates Falcon signature generation

### 4. Low-Latency FFT/iFFT RTL (Ortega et al.)
- **Paper**: 2025
- **Authors**: A. Ortega et al.
- **Type**: Full RTL implementation of FFT and inverse FFT for FALCON
- **Platform**: FPGA
- **Notes**: First full RTL implementation addressing FALCON's unusual requirements

---

## Saber Implementations

### 1. sujoyetc/SABER_HW
- **Repository**: https://github.com/sujoyetc/SABER_HW
- **Language**: VHDL (48.4%), C (25.3%), SystemVerilog (4.0%), Verilog (1.5%)
- **Platform**: FPGA (Xilinx UltraScale+ XCZU9EG-2FFVB1156)
- **Type**: Instruction set coprocessor architecture with full CCA transformations
- **License**: Academic research use only
- **Performance** (module dimension 3, AES-192 security):
  - Key generation: 5,453 cycles
  - Encapsulation: 6,618 cycles
  - Decapsulation: 8,034 cycles
  - Clock frequency: 250 MHz
- **Resources**:
  - LUTs: 23,686
  - FFs: 9,805
  - BRAMs: 2 tiles
  - Keccak core: 5,113 LUTs, 3,068 FFs
- **Features**: Parallel polynomial multiplier (256 cycles for full multiplication), optimized memory access
- **Paper**: https://eprint.iacr.org/2020/434.pdf
- **Tools**: Vivado 2018.1
- **Side-channel countermeasures**: Not mentioned
- **Notes**: Fastest hardware implementation of Saber at time of publication

### 2. Centre-for-Hardware-Security/saber-chip
- **Repository**: https://github.com/Centre-for-Hardware-Security/saber-chip
- **Type**: ASIC conversion from RTL code
- **Notes**: Based on sujoyetc/SABER_HW

---

## NTRU Implementations

### 1. AdrianMarotzke/SNTRUP_on_FPGA
- **Repository**: https://github.com/AdrianMarotzke/SNTRUP_on_FPGA
- **Language**: VHDL (49.9%), Verilog (49.6%)
- **Platform**: FPGA (Xilinx Zynq Ultrascale+, Xilinx Artix-7)
- **Type**: Constant-time hardware implementation of Streamlined NTRU Prime (sntrup761)
- **License**: MIT
- **Paper**: https://eprint.iacr.org/2021/1444
- **Performance** (sntrup761 on Zynq Ultrascale+):
  - **High-speed design**:
    - Key Gen: 64,026 cycles @ 285 MHz = 224.7 µs (6,038 slices, 37,813 LUTs, 33 BRAMs, 23 DSPs)
    - Encap: 5,007 cycles @ 289 MHz = 17.3 µs (5,381 slices, 31,996 LUTs, 4.5 BRAMs, 6 DSPs)
    - Decap: 10,989 cycles @ 285 MHz = 38.6 µs (5,432 slices, 32,301 LUTs, 3.5 BRAMs, 9 DSPs)
  - **Low-area design**:
    - Key Gen: 629,367 cycles @ 285 MHz = 2,208 µs (1,232 slices, 7,216 LUTs, 5.5 BRAMs, 12 DSPs)
    - Encap: 29,245 cycles @ 290 MHz = 100.8 µs (1,074 slices, 6,030 LUTs, 4.5 BRAMs, 7 DSPs)
    - Decap: 85,628 cycles @ 283 MHz = 302.6 µs (1,051 slices, 6,016 LUTs, 3 BRAMs, 7 DSPs)
- **Features**: Batch key generation support, configurable vector width, constant-time implementation
- **Verification**: Tested against NIST KAT files (50 test vectors)
- **Side-channel countermeasures**: Constant-time design
- **Notes**: Includes SHA-512 implementation, supports parameter sets configuration

### 2. Streamlined NTRU Prime (Peng et al.)
- **Paper**: "Streamlined NTRU Prime on FPGA" (2023)
- **Authors**: B.Y. Peng et al.
- **Type**: Novel full hardware implementation with high-speed and low-area variants
- **Citation count**: 20+

---


## Side-Channel Protected Implementations

### 1. PRASANNA-RAVI/SCA_protected_Kyber
- **Repository**: https://github.com/PRASANNA-RAVI/SCA_protected_Kyber
- **Platform**: ARM Cortex-M4 (software, but relevant for understanding countermeasures)
- **Type**: Side-channel attack resistant implementation
- **License**: Not explicitly stated
- **Countermeasures**:
  - **Shuffled NTT**: Randomizes order of butterfly operations within each NTT stage
  - **Randomized NTT**: Multiplicative masking of twiddle factors (low-entropy masking)
  - **Shuffled-Randomized NTT**: Combined approach
  - **Shuffling of secret-sensitive operations**: Applied to polynomial operations
- **Protection Levels**: 4 levels (0=unprotected, 1=shuffled, 2=randomized, 3=combined)
- **Framework**: Based on pqm4 library
- **Notes**: First round Kyber implementation; countermeasures applicable to hardware designs

### 2. masked-kyber-m4/mkm4
- **Repository**: https://github.com/masked-kyber-m4/mkm4
- **Platform**: ARM Cortex-M4 (software)
- **Type**: First-order masked Kyber implementation
- **Paper**: "Masking Kyber: First- and Higher-Order Implementations" (TCHES)
- **Citation count**: 146+
- **Features**: First completely masked implementation with formal proofs in probing model
- **Notes**: Techniques applicable to hardware masking

### 3. uclcrypto/pqm4_masked
- **Repository**: https://github.com/uclcrypto/pqm4_masked
- **Platform**: ARM Cortex-M4 (software)
- **Type**: Masked implementations of PQ crypto library
- **Algorithms**: Kyber768, Saber
- **Notes**: Research paper available

### 4. Masked Pure-Hardware Kyber (Kamucheka et al.)
- **Paper**: "A Masked Pure-Hardware Implementation of Kyber Cryptoprocessor" (NIST PQC 2022)
- **Authors**: T. Kamucheka et al.
- **Type**: Pure hardware masked implementation of Kyber-512
- **Platform**: FPGA
- **Features**: Novel hybrid hiding-masking scheme, demonstrably secure against power analysis
- **Citation count**: 25+
- **Notes**: First pure-hardware masked Kyber implementation

### 5. A Masked Implementation of CRYSTALS-Kyber (Reparaz et al.)
- **Paper**: TCHES 2022
- **Authors**: O. Reparaz, S. M. T. Islam, R. de Clercq, I. Verbauwhede
- **Type**: Masked implementation with formal security analysis
- **Notes**: Influential work on masking lattice-based schemes

---

## Summary Notes

### Key Observations:
1. **Most active repositories**: Kyber and Dilithium have the most open-source RTL implementations
2. **Dominant languages**: VHDL and Verilog are primary, with increasing HLS (C++) adoption
3. **Common platforms**: Xilinx FPGAs (Artix-7, Zynq, UltraScale+) dominate
4. **License diversity**: Mix of academic-only, MIT, and open-source hardware licenses
5. **Side-channel countermeasures**: Limited availability in open-source RTL; mostly software-based masked implementations
6. **Performance focus**: Most implementations prioritize speed over area or security
7. **Verification**: Most implementations verified against NIST KAT files

### Missing/Limited RTL Implementations:
- **FALCON**: Very limited full RTL implementations (mostly FFT cores only)
- **SPHINCS+**: Few hardware implementations, mostly hash core focused
- **Side-channel secure RTL**: Very few open-source masked hardware implementations
- **ASIC implementations**: Most are FPGA-focused; ASIC results mostly in papers without open RTL

