# Cache Analysis of RISC-V RV64 Binaries in Gem5  

This repository explores the **analysis and improvement of cache performance** for C program binaries compiled using the **RISC-V RV64 toolchain**.  
It involves building a RISC-V cross-compilation toolchain, compiling programs, and simulating their execution in **Gem5** to study cache behavior.  

---

## Building the RISC-V Toolchain  

The **RISC-V GNU toolchain** allows you to compile C/C++ programs into RISC-V binaries.  
Here, we enable **multilib support**, which provides flexibility to compile programs targeting both 32-bit and 64-bit RISC-V architectures.  

```bash
# Enter the toolchain folder
cd riscv-gnu-toolchain        

# Configure the toolchain
./configure --prefix=$HOME/riscv --enable-multilib  
# --prefix specifies installation directory ($HOME/riscv)  
# --enable-multilib allows support for multiple ISAs (32-bit and 64-bit)  

# Build the toolchain
make -j$(nproc)  
# Uses all available CPU cores for faster compilation  
# On lower-end PCs, use -j4 or -j6 instead  

# Add the toolchain binaries to PATH
echo 'export PATH=$HOME/riscv/bin:$PATH' >> ~/.bashrc  
source ~/.bashrc
# Ensures global access to RISC-V compilers (riscv64-unknown-elf-gcc, etc.)
