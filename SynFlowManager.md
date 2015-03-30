# syn: A run-in-batch flow manager for synthesis #
## USAGE: ##
`./syn <Architecture List> <Bypass List> <Depth List> <Width List> <#Write Ports List> <#Read Ports List>`

  * Use a comma delimited list; no spaces; can be surrounded by brackets ()[.md](.md){}<>
  * RAM depth, width, number of read/write ports and cycles are positive integers
  * Architecture is one of: REG, XOR, LVTREG, LVTBIN, or LVT1HT
    * REG   : Register-based multi-ported RAM
    * XOR   : XOR-based multi-ported RAM
    * LVTREG: Register-based LVT multi-ported RAM
    * LVTBIN: Binary-coded I-LVT-based multi-ported RAM
    * LVT1HT: Onehot-coded I-LVT-based multi-ported RAM
  * Bypass list is one of: NON, WAW, RAW, or RDW
    * WAW: Allow Write-After-Write (need to bypass feedback RAM)
    * RAW: new data for Read-after-Write (need to bypass output RAM)
    * RDW: new data for Read-During-Write

## EXAMPLES: ##
  * `./syn XOR NON 1024 32 3 2`
    * Synthesis a XOR-based RAM with no bypassing; 1K lines RAM; 32 bits width; 3 write & 2 read ports
  * `./syn LVTBIN,LVT1HT RAW,RDW 512,1024 8,16,32 2,3,4 1,2,3,4`
    * Synthesis LVTBIN and LVT1HT RAMs with new data RAW and RDW bypassing; 512 and 1024 lines; 8,16, and 32 data width; 2,3, and 4 write ports; 1,2,3, and 4 read ports. Total of 144 RAM combinations.

The following files and directories will be created after compilation:
  * syn.res : A list of results, each run in a separate line, including: frequency, resources usage, and runtime
  * log/    : Altera's logs and reports