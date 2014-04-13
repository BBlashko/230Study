230Study
========


1) Performance (Clock Cycles etc...) 

    CPI = CPU clock cycles/Instruction Count
	Clock rate = 1/ P (clock cycle)
    CPU time = (IC * CPI)/Clock rate
	 or !!!
	CPU time = (IC * CPI) * P(clock cycle time) 
    
2) Virtual Memory 

    Virtualizes all storage, makes it appear as one large memory device
    Benefits: - Provides illusion of unbounded amount of memory
              - Provides relocation, programs can be loaded into any location
              
    Only use RAM for "active" code and data, store everything else on disk
        - Few programs need all their code and data at once
    Physical memory holds a small number of virtual 'pages' in physical page 'frames'
    Page table in memory or Memory Management Unit (MMU)
    Each program has its own page table
    ## Page valid in page tbl, entry+offset = physical page number in memory
    SLIDES 26-30 ON VIRTUAL TO UNDERSTAND PAGE#OFFSET

3) Memory

    Static RAM (REGISTERS AND CACHE)
      - FAST, MORE EXPENSIVE (both space and manufacturing)
      - No refreshing needed when powered
    Dynamic RAM (MAIN MEMORY) 
      - SLOW, LESS EXPENSIVE
      - MORE DENSE
      - needs refreshing when powered (every 16-64 ns)
    
3) Cache 

    Temporal Locality
      - When info accessed, high probability it will be accessed again
    Spatial Locality
      - When info accessed, high probability nearby info will be accessed
      
    L1 (Primary) Cache
      - Smaller
      - Optimizes hit time to have shorter clock cycle 
    L2 (Secondary) Cache
      - Larger (access time less critical)
      - Optimizes miss rate to reduce time penalty of cache miss
      
    # Disk Access Time = Rotation Time + Seek Time
      Average access time from CPU =
        hit rate * cache access time + (1 - hit rate) * miss penalty
    
    
4) Linkers, Loaders, Compilers

    Loader
        - Copies .exe into main memory for execution
        - Initialize registers and set stack pointer
        - Use symbol table to look up _start address, get ready for execution
        
    When the linker combines .o files, check for unresolved external references...    
    Static Linking
      - Linked at runtime, library subroutines are part of .exe
    Dynamic Linking 
      - Unresolved references replaced to reference of 'stub' routine 
            - First time: copies missing function into main memory
            - Missing function overwrites stub routine, next call directly to function   
      - Linked as needed
      - Executable is smaller
      
5) Fetch, Decode, Execute  
    WHOLE CYCLE IS...
	FETCH STEP:
		- Address in PC -> MAR
		- MAR -> Address Bus
		- Read Signal -> Control Bus
		- Wait for memory (increment PC, using ALU) *UPDATE STEP*
		- Content of location from memory -> Data Bus
		- Data Bus -> MDR -> IR
	DECODE STEP:
		- Looks at opcode and operands in IR
		- Decoder part of Control Unit of CPU
	POSSIBLY MORE FETCHES FOR MORE OPERANDS
	EXECUTE STEP:
		- May involve ALU / Read and writes to memory
	REPEAT!!!!	
	
6) Pipelining 

	Increases performance by increasing instruction throughput 
	N instructions, each take m cycles..
	Without pipelining:
		- Time = N*m
	With pipelining:
		- Time = m + N -1
    Speedup = ~m (A new instruction is started every clock cycle)
	Instruction Hazard:
		- An instruction is not yet available
	Data Hazard:
		- required operand is not yet available (r3 being added, next instruction loads r3, which isn't ready yet)
	Structural Hazard:
		- when two resources need access to same hardware resource
	BIG PENALTY FOR INTERRUPTING PIPELINE (BRANCHING)
		- Penalty = # of idle cycles caused by branch
		
7) Parallelism 

	Flynn Taxonomy 
		Single Instruction Single Data (SISD)
			- Uniprocessor
		Single Instruction Multiple Data (SIMD)
			- Vector/Array processing 
		Multiple Instruction Single Data (MISD) (useless?)
		Multiple Instruction Multiple Data (MIMD)	
   
	Tight Coupling
		- Heavy reliance on other systems
	Loose Coupling 
		- More independence

	Amdahl's Law for speedup: (MAX SPEEDUP OF 20 ASSUMING 95% PARALELL INSTRCUTIONS) 
		Speedup = 1 / (f + ((1-f)/P)) 
			f = % of sequential instructions 
			P = # of processors 
   
<br>
  ASSIGNMENTS
  
1)

  Address
  
2) 


4)
  Virtual Memory


Files to keep track of studying for 230
