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
   * spechmmer
   * sjeng
   * htr
3. Benchmarks:
   * dtdgn
   * sth
   * spechmmer
   * sjeng
   * htr
4. gbdrgb

## Second Section

1.dfbdfsb
2.fvefvs

## Third Section

