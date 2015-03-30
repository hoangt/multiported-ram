# sim: A run-in-batch flow manager for simulation #

## USAGE: ##

`./sim <Depth List> <Width List> <#WritePorts List> <#ReadPorts List> <#Cycles>`

  * Use a comma delimited list; no spaces; can be surrounded by brackets ()[.md](.md){}<>
  * RAM depth, width, number of read/write ports and cycles are positive integers

## EXAMPLES: ##
  * `./sim 1024 32 3 2 1000000`
    * Simulate 1M cycles of a 1K lines RAM, 32 bits width, 3 write & 2 read ports
  * `./sim 512,1024 8,16,32 2,3,4 1,2,3,4 1000000`
    * Simulate 1M cycles of RAMs with 512 or 1024 lines, 8, 16, or 32 bits width, 2,3, or 4 write ports, 1,2,3, or 4 read ports. Total of 72 RAM combinations

The following files and directories will be created after simulation:
  * sim.res : A list of simulation results, each run in a separate line, including all design styles