230Study
========


1) Performance (Clock Cycles etc...) 
    
    CPI = CPU clock cycles/Instruction Count
    CPU time = (IC * CPI)/Clock rate
    
    
    # What is speedup formula?!
    
2) Virtual Memory 

    NEEDS WORK


3) Memory

    Static RAM (REGISTERS AND CACHE)
      - FAST, MORE EXPENSIVE (both space and manufacturing)
      - No refreshing needed when powered
    Dynamic RAM (MAIN MEMORY) 
      - SLOW, LESS EXPENSIVE
      - MORE DENSE
      - needs refreshing when powered (every 16-64 ns)
    
3) Cache  ******

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
      - Unresolved references replaced to referebce of 'stub' routine 
            - First time: copies missing function into main memory
            - Missing function overwrites stub routine, next call directly to function   
      - Linked as needed
      - Executable is smaller
      
5) Fetch, Decode, Execute      
    
<br>
  ASSIGNMENTS
  
1)

  Address
  
2) 


4)
  Virtual Memory


Files to keep track of studying for 230
