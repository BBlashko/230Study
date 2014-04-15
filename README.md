230Study
========

0) Logical shifts = Unsigned
   Arithmetic shifts = Signed	
	

1) Performance (Clock Cycles etc...) 

    CPI = CPU clock cycles/Instruction Count
	Clock rate = 1/ P (clock cycle)
    CPU time = (IC * CPI)/Clock rate
	 or !!!
	CPU time = (IC * CPI) * P(clock cycle time)
    Performance = 1 / Execution Time		
    Multicore
    	- 2 CPUs, 1 cache, 1 MMU
    Multiprocessor
    	- 2 CPUS, 2 caches, 2 MMU
	
    
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
      
    Volatile Memory
      - Computer memory that requires power to retain its stored information.
    Non-Volatile Memory 
      - Computer memory that does not need power to retain its stored information.
    
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
        
    Associative Cache (ANYONE CAN PARK ANYWHERE)
    	- A block is placed in *any* location in cache
    	- reduces miss ratio
    	- all entries in cache must be searched in parallel (hardware does it)
    	- Most flexible, most expensive
    Direct-Mapped Cache	
        - (Block address)%(Number of cache blocks)
        	- similar to hash table	
    Another Design Concept: Split cache
    	- One cache for Instructions (I cache)
    	- Seperate cache for Data (D cache)
    In general, average access time from CPU = ...
    	= hitRate * cache access time + (1-hitRate)*missPenalty
    Unit of data transfer for Cache is a 'SET' or 'BLOCK'
    
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
							     |--> MISD is hardly used
		Multiple Instruction Multiple Data (MIMD)	
   
	Tight Coupling
		- Heavy reliance on other systems
	Loose Coupling 
		- More independence

	Amdahl's Law for speedup: (MAX SPEEDUP OF 20 ASSUMING 95% PARALELL INSTRCUTIONS) 
		Speedup = 1 / (f + ((1-f)/P)) 
			f = % of sequential instructions 
			P = # of processors 
			
8) I/O Basics
				
	Bus Basics
	Bus inside a processor is called a 'datapath'
	Busses can be...
		- Asynchronous
			- not clocked, good for variety of devices
			- needs handshaking protocol
		- Synchronous (Usually only for memory) 
			- fixed handshake protocol relative to clock
			- fast; little hardware
	Interfaces and Devices
		- Brute Force
		- Handshake
	Processor and Interface
		- Polling Driven
		- Interrupt Driven

9) System Organization 

	Computer Architecture 
		- functional behaviour as viewed by programmer (ex. word size)
	Computer Organization 
		- Structural stuff not visible to programmer
	Processor (CPU) includes...
		- Control Unit
		- Registers 
		- ALU	
	Bus Structures
		Port I/O (Older, mainly Intel)
			- Seperate buses for CPU -> Memory and CPU -> Peripherals 
		Memory Mapped I/O
			- Single bus between CPU and all other components
			- Locations 'indexed' (ex. room 526 infers 5th floor)
			
10) Interrupts

	Internal (to CPU)
		- Software errors (ex. divison by 0)
		- Called 'exceptions'
	External (to CPU)
		- (ex. a peripheral generates an event)
		- Called an 'interrupt'
	Interrupts are NOT scheduled
	BASIC SAMPLE SEQUENCE..
	1) External device asserts "Interrupt" with a signal on the interrupt line
	2) CPU stops and enters a 'general interrupt service routine (ISR)
	3) CPU disables interrupt bits
	4) CPU sends an acknowledgement to the device
	5) Device resets the interrupt line signal
	6) CPU services "interrupt" with appropriate ISR
	7) CPU re-enables Interrupt bits
	8) CPU resumes computing
	# WHAT ARE INTERRUPT VECTORS???
		- starting address of ISR for every device allowed to interrupt
		- Interrupt table contains all interrupt vectors
	
<br>
  ASSIGNMENTS
  
1)

  Address
  
2) 


4)
  Virtual Memory


Files to keep track of studying for 230
