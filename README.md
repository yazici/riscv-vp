RISC-V based Virtual Prototype
==============================

The RISC-V based Virtual Prototype (VP) integrates a RISC-V RV32IM core, a PLIC-based interrupt controller and an essential set of peripherals together with SW debug capabilities. The VP is designed as extensible and configurable platform with a generic bus system and implemented in standard-compliant SystemC and TLM-2.0. For more information please visit http://www.systemc-verification.org/ or contact <riscv@systemc-verification.org>. In the following we provide build instructions and how to compile and run software on the VP.


1) Build the RISC-V GNU Toolchain:
----------------------------------

(Cross-)Compiling the software examples, in order to run them on the VP, requires the RISC-V GNU toolchain to be available in PATH. It can be build as follows:

```bash
git clone https://github.com/riscv/riscv-gnu-toolchain.git
cd riscv-gnu-toolchain
git submodule update --init --recursive

./configure --prefix=$(pwd)/../riscv-gnu-toolchain-dist-rv32g-ilp32d --with-arch=rv32g --with-abi=ilp32d

make
```


2) Build this RISC-V Virtual Prototype:
---------------------------------------

i) in *vp/dependencies* folder (will download and compile SystemC):
 
```bash
./build_systemc_232.sh
```
 
 	
ii) in *vp* folder:
 
```bash
mkdir build
cd build
cmake ..
make
```

 	
3) Compile and run some SW:
---------------------------
	
In *sw*:

```bash
cd simple-sensor    					# can be replaced with different example
make									# (requires RISC-V GNU toolchain in PATH)
../../vp/build/lib/riscv-vp main		# shows final simulation time as well as register and pc contents
```

Add the *riscv-vp* executable to PATH to simplify execution of SW examples.