# Cache-Analysis-of-RISC-V-RV64-Binaries-in-Gem5
This Repository explores and dives into the analysis and improvement of Cache for C programs binaries compiled using RISC-V RV64 toolchain

#Building the toolchain:

# Cache-Analysis-of-RISC-V-RV64-Binaries-in-Gem5  

This Repository explores and dives into the analysis and improvement of Cache for C programs binaries compiled using RISC-V RV64 toolchain  

---

## Building the toolchain  

```bash
cd riscv-gnu-toolchain        # entering the toolchain folder  

./configure --prefix=$HOME/riscv --enable-multilib  
# this configures the toolchain for multi-lib support  
# multilib is basically supoort for multiple extensions and other base ISA like 32-bit  
# so even if your toolchain is 32 bit you can compile and get 64 bit binaries and vice-versa  

make -j$(nproc)  
# make/build with all resources used for parallel processes, use j4 j6 on lower end PC's  

echo 'export PATH=$HOME/riscv/bin:$PATH' >> ~/.bashrc  
# gives the path of the toolchain globally  

source ~/.bashrc  


# similarly building gem5
cd ../gem5
scons build/RISCV/gem5.opt -j$(nproc)

