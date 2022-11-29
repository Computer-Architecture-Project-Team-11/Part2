# Advanced Computer Architecture Project - Part 2

## First Section
1. From the `config.ini` file we found the following information:
      * L1 instruction cache: 
        ```
        [system.cpu.icache]
         assoc=2
         size=32768
        ```
      * L1 data cache: 
        ```
        [system.cpu.dcache]
         assoc=2
         size=65536
        ```
      * L2 cache: 
        ```
        [system.l2]
         assoc=8
         size=2097152
        ```
      * Cache Line: 
        ```
        [system]
         cache_line_size=64
        ```
2. For every benchmark the following information can be found in their respective `stats.txt` files:
   * **specbzip**  
     i) **Execution time**:
     ```python
     sim_seconds                                  0.083982                       # Number of seconds simulated
     ```
     ii) **CPI**
     ```python
     system.cpu.cpi                               1.679650                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.000077                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.014798                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.282163                       # miss rate for overall accesses
       ```
   * **specmcf**  
     i) **Execution time**:
     ```python
     sim_seconds                                  0.064955                       # Number of seconds simulated
     ```
     ii) **CPI**:
     ```python
     system.cpu.cpi                               1.299095                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.023612                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.002108                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.055046                       # miss rate for overall accesses
       ```
   * **spechmmer**

     i) **Execution time**:
     ```python
     sim_seconds                                  0.059396                       # Number of seconds simulated
     ```
     ii) **CPI**:
     ```python
     system.cpu.cpi                               1.187917                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.000221                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.001637                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.077760                       # miss rate for overall accesses
       ```
   * **sjeng**

     i) **Execution time**:
     ```python
     sim_seconds                                  0.513528                       # Number of seconds simulated
     ```
     ii) **CPI**:
     ```python
     system.cpu.cpi                               10.270554                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.000020                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.121831                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.907550                       # miss rate for overall accesses
       ```
   * **speclibm**

      i) **Execution time**:
     ```python
     sim_seconds                                  0.513528                       # Number of seconds simulated
     ```
     ii) **CPI**:
     ```python
     system.cpu.cpi                               10.270554                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.000020                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.121831                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.907550                       # miss rate for overall accesses
       ```
3. For all benchmarks the following values were equal with the respective changes in the frequency:
      * Default frequency
         * System cpu clock
          ```python 
          system.cpu_clk_domain.clock                       500                       # Clock period in ticks
          ```
         * System clock
          ```python 
          system.clk_domain.clock                          1000                       # Clock period in ticks
          ```
      * 1GHz
         * System cpu clock
          ```python 
          system.cpu_clk_domain.clock                       1000                       # Clock period in ticks
          ```
         * System clock
          ```python 
          system.clk_domain.clock                          1000                       # Clock period in ticks
          ```
      * 3GHz
         * System cpu clock
          ```python 
          system.cpu_clk_domain.clock                       333                       # Clock period in ticks
          ```
         * System clock
          ```python 
          system.clk_domain.clock                          1000                       # Clock period in ticks
          ```
      There seems to be an inversely proportional relation between the frequency and the System cpu clock. This means that the default frequency is set to 2GHz.

4. Changing the memory type from `DDR3_1600_x64` to `DDR3_2133_x64` to the sjeng benchmark there seems to be a slight decreament in the simulated time:
   ```python 
      sim_seconds                                  0.513528                       # Number of seconds simulated
      sim_seconds                                  0.493128                       # Number of seconds simulated
    ```
   which is expected since the second memory type has a quicker clock. Also we observed that the cycles simulated are also decreased:

      
       system.cpu.numCycles                       1027055373                       # number of cpu cycles simulated
       system.cpu.numCycles                        986256235                       # number of cpu cycles simulated
    

## Second Section

1.dfbdfsb
2.fvefvs

## Third Section

