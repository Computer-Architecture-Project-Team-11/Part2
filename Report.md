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
     sim_seconds                                  0.174671                       # Number of seconds simulated
     ```
     ii) **CPI**:
     ```python
     system.cpu.cpi                               3.493415                       # CPI: cycles per instruction
     ```
     iii) **Overall miss rates**:
       * L1 Instruction cache:
       ```python
       system.cpu.icache.overall_miss_rate::total     0.000094                       # miss rate for overall accesses
       ```
       * L1 Data cache:
       ```python
       system.cpu.dcache.overall_miss_rate::total     0.060972                       # miss rate for overall accesses
       ```
       * L2 cache:
       ```python
       system.l2.overall_miss_rate::total           0.999944                       # miss rate for overall accesses
       ```
   Below are presented the plots for each parameter comparing each benchmark:
    * Execution Time

    ![Screenshot from 2022-11-29 21-56-18](https://user-images.githubusercontent.com/105559292/204636530-5fa199a2-860a-4463-91e3-4c82d2fa8c2d.png)

    * Cycles per Instruction

    ![cpi](https://user-images.githubusercontent.com/105559292/204637624-b4095544-9e93-4476-bdd8-ec6a75771440.png)


    * L1 Instruction Cache Miss Rate

    ![Screenshot from 2022-11-29 21-59-17](https://user-images.githubusercontent.com/105559292/204636575-6f5774f0-7178-4da5-8e13-f6f262694919.png)

    * L1 Data Cache Miss Rate

    ![L1 data](https://user-images.githubusercontent.com/105559292/204637663-4749d493-2deb-4920-bbbe-56827fbb926a.png)


    * L2 Cache Miss Rate

    ![Screenshot from 2022-11-29 22-01-40](https://user-images.githubusercontent.com/105559292/204636648-2ad317ff-af8f-44a9-82ea-a51dcc4581aa.png)

   From the graphs we can see that the values of Execution Time and Cycles per Instruction are significantly higher for the sjeng and speclibm benchmarks. This happens because as we see from the miss rates below, these two benchmarks are the only ones with two out three high miss rates (l1 data chache miss rate and l2 cache miss rate). The miss rates as well as the respective access time affect the CPI. So with higher miss rates, higher CPI and Execution Time are expected. 

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
      There seems to be an inversely proportional relation between the frequency and the System cpu clock. Apparently, when a new frequency is given in the command           line, the new system cpu clock is determined by dividing the system clock with the new frequency. Considering this information we can assume that the original         frequency is set to 2GHz. We can, also, deduce that when the frequency is changed (1GHz/3GHz) only the system cpu clock is affected, while the system clock             remains the same(default GHz). This behaviour can be explained if we consider that the system clock synchronizes all the components of our computer, while the         cpu clock is used just for the processor.
      
      If we added a new processor, it would most likely be affected by the change of the frequency and have a different cpu clock, since it is a new CPU and has a           seperate clock from the rest of the system. 
      
      Based on the execution times we can see that as the frequency increases the execution time decreases. Though, the execution time is not decreasing proporsionaly as we observed with the cpu.clock above. There is not a scalling regarding the execution time because there is not a 1-1 relation between them. The execution time cannot decrease as easily. modifing only one system parameter, but it is affected by a lot others too. 
      

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

References:
  * [Difference between CPU clock and system clock](https://cs.stackexchange.com/questions/32149/what-are-system-clock-and-cpu-clock-and-what-are-their-functions)
  * [Caches affection on CPI](https://courses.cs.washington.edu/courses/cse378/07au/lectures/L18-Cache-Wrap-up.pdf)
  * [Miss rate relation to CPI](https://courses.cs.washington.edu/courses/cse378/07au/lectures/L18-Cache-Wrap-up.pdf)
