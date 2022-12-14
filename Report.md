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

    | Parameters | specbzip | specmcf | spechmmer | sjeng | speclbm |
    | ------ | ------ | ------ | ------ | ------ | ------ |
    | Execution time | 0.083982  | 0.064955  | 0.05936 | 0.513528 | 0.174671 |
    | CPI | 1.679650  | 1.299095  | 1.187917 | 10.270554 | 3.493415 |
    | L1 Instruction cache miss rates | 0.000077  | 0.023612 | 0.000221 | 0.000020 | 0.000094 |
    | L1 Data cache miss rates | 0.014798 |  0.002108  | 0.001637 | 0.121831 | 0.060972 |
    | L2 cache miss rates | 0.282163  | 0.055046 | 0.077760 | 0.907550 | 0.999944 |

     
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

1. We run 10 simulations for the first benchmark to test the affection that the parameters had on the CPI. Then for each of the rest of the benchmarks we run 5 simultations adjusting the changes on the values of the parameters accordingly.
2. Graphs for each benchmark about the affections of the parameters on the CPI
   * spec_bzip

      ![bzip](https://user-images.githubusercontent.com/105559292/205138100-ff6c7e3b-1652-4f1f-a179-07400f29563e.png)
 
   * spec_mcf

      ![mcf](https://user-images.githubusercontent.com/105559292/205138145-14d4632e-4e2c-4ac4-b911-65dc28de43c1.png)

   * spec_hmmer

      ![hmmer](https://user-images.githubusercontent.com/105559292/205138201-2deb28b7-6e57-42f1-a883-23631ba52dbb.png)

   * spec_sjeng

      ![sjeng](https://user-images.githubusercontent.com/105559292/205138267-a0d94604-05df-47ea-b851-1513bfe90510.png)

   * spec_lbm

      ![lbm](https://user-images.githubusercontent.com/105559292/205138317-ed8bf824-37be-418d-9537-8a310cf11497.png)


Based on the results shown on the graphs and general information and knowlegde regarding the CPI we extracted the following conclusions:
   * the value of the CPI is highly connected with the **miss rates**. So to achieve a low CPI value we tried to decrease the miss rates.
   * we observed that th increament of the **caches' sizes** and **associativities** contribute to lowering the miss rates. And this means that we have a lower CPI value too.
   * decreasing the **cache line size** resultes in higher CPI as tested in the first benchmark. Instead by increasing the cache line size we managed to decrease the value of the CPI

## Third Section

Function reagrding the balnce between cost and performance:

> ## Cost = cache_line_size/16 + 10^(-3) * l1_size + l1_assoc / 100 + 10^(-6) * l2_size + l2_assoc /100
                              
- as l1 we have inlcuded both li and ld. 

Why we ended up in the equation above:

* As the size of the Cache increases the effect of small associativity of this cache on time and speed is similar to a bigger associativity.
* L1 cache is more "expensive" than L2.
* The size of the cache line has the same effect as the size of the cache on the perforamnce with different associativity values. As the size increases the different values of the associativity seem to have similar results as far as time and speed are concerned. 
* In general larger cache sizes tend to have worse results regarding the speed and time.

The table below presents the "Cost", based no the above function, and the best option result. The best option value is the result of the division of the Cost of each change with the previously calculated CPI decreament (performance). The smaller value for each benchmark indicates the changes that need to be made in order to achive a good performane, keeping a low "Cost". The "Cost" of the default parameter values is `102,1`.

    | Parameters | Cost | specbzip | specmcf | spechmmer | sjeng | speclbm |
    | ------ | ------ | ------ | ------ | ------ | ------ | ------ |
    | x2 cache line size |  106,1 | 1.666573  | 1.330534 | 0.513528 | - | 2.581299 |
    | x2 l1 size and assoc | 198,12  | 1.642654  | 1.154963 | 10.270554 | 3.493415 | 3.493293 |
    | x2 cache line size and l1 size and assoc | zrshe  | - | - | 0.000020 | 0.000094 | - |
    | x2 cache line size and l1 size, assoc and l2 assoc | 202,2  | 1.617843 | 1.123168 | 0.000020 | 6.799610 | 2.581254 |
    | x4 cache line size and x2 l1 size, assoc and l2 assoc | dshsth  | - | - | 0.000020 | 5.175560 | - |
    | x4 cache line size and l2 assoc and x2 l1 size, assoc | sthdt | - | - | 0.000020 | 5.175560 | - |

Taking all these into consideration we have understood that our choices on the paramters of the benchmarks in section 2, although they were effective on lowering the CPI, they are not as efficient regarding the possible "costs". (specifically we have choosen a really large size for the l1 cache)

References:
  * [Difference between CPU clock and system clock](https://cs.stackexchange.com/questions/32149/what-are-system-clock-and-cpu-clock-and-what-are-their-functions)
  * [Caches affection on CPI](https://courses.cs.washington.edu/courses/cse378/07au/lectures/L18-Cache-Wrap-up.pdf)
  * [Miss rate relation to CPI](https://courses.cs.washington.edu/courses/cse378/07au/lectures/L18-Cache-Wrap-up.pdf)
  * [Associativity](https://en.algorithmica.org/hpc/cpu-cache/associativity/)
  * [Associativities Advantages and Disadvantages](https://en.wikipedia.org/wiki/Cache_placement_policies#Direct-mapped_cache)
  * Αρχιτεκτονική Υπολογιστών: Μια ποσοτική προσέγγιση, 6η Αμερικάνικη Έκδοση, John L. Hennessy, David A. Patterson, σελ. 121, Εικόνα 2.8
