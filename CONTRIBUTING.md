# How to Contribute

We welcome contributions to the PQC RTL Benchmarking Framework! Here’s how you can help.

## Adding a New Implementation

1.  **Fork and Clone**: Fork the repository and clone it to your local machine.

2.  **Edit `configs/implementations.yaml`**: This is the central registry for all PQC implementations. Find the correct algorithm key (e.g., `kyber`, `dilithium`) and add a new entry for the implementation you want to add.

    **Required Fields**:

    -   `name`: A unique, descriptive name for the implementation (e.g., `author-scheme-fpga`).
    -   `repo`: The full Git URL of the repository.
    -   `type`: The type of implementation. Choose from:
        -   `full_accelerator`: A complete PQC accelerator.
        -   `polynomial_multiplier`: An NTT or polynomial multiplication core.
        -   `hash_accelerator`: A SHA-3/SHAKE accelerator.
        -   `hw_sw_codesign`: A hardware/software co-design.
    -   `platform`: The target platform (`fpga`, `asic`, `zynq`).
    -   `language`: The primary HDL (`verilog`, `vhdl`, `hls`).

    **Optional Fields**:

    -   `target_device`: The specific FPGA device targeted (e.g., `artix7`, `zynq_ultrascale_plus`).
    -   `security_levels`: A list of supported security levels (e.g., `[512, 768, 1024]` for Kyber).
    -   `sca_protected`: `true` or `false`.
    -   `sca_type`: If protected, the type of countermeasure (`constant_time`, `masking`).
    -   `build_system`: The build system used (`vivado`, `vitis_hls`, `make`).
    -   `notes`: Any additional information.

3.  **Test Your Changes**: Run the benchmark for the new implementation to ensure it works as expected.

    ```bash
    make benchmark-<algorithm>
    ```

4.  **Submit a Pull Request**: Once you are satisfied with your changes, submit a pull request to the main repository.

## Improving the Framework

We are always looking for ways to improve the benchmarking framework. Here are some areas where you can contribute:

-   **Improving Synthesis Scripts**: Enhance the `vivado_synth_template.tcl` to be more robust and support more complex projects.
-   **Adding Support for More Simulators**: Add support for other simulators like ModelSim or VCS.
-   **Improving Report Generation**: Enhance the `report_generator.py` to create more insightful visualizations or analyses.
-   **Bug Fixes**: Find and fix bugs in the existing scripts.

Thank you for contributing!
