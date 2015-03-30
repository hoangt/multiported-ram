# Multi-ported RAM module instantiation #

All **.v &**.vh files in this package should be copied into your work directory.
Copy the following instantiation, change parameters and connectivity to fit your design.
```
   // instantiate a multiported-RAM
mpram #( .MEMD   (MEMD   ),  // positive integer: memory depth
         .DATAW  (DATAW  ),  // positive integer: data width
         .nRPORTS(nRPORTS),  // positive integer: number of reading ports
         .nWPORTS(nWPORTS),  // positive integer: number of writing ports
         .TYPE   (TYPE   ),  // text: multi-port RAM implementation type:
                             //   "AUTO"  : Choose automatically
                             //   "REG"   : Register-based
                             //   "XOR"   : XOR-based
                             //   "LVTREG": Register-based LVT
                             //   "LVTBIN": Binary-coded I-LVT-based
                             //   "LVT1HT": Onehot-coded I-LVT-based
         .BYP    (BYP    ),  // text: Bypassing type:
                             //   WAW: Allow Write-After-Write
                             //        (need to bypass feedback ram)
                             //   RAW: New data for Read-after-Write
                             //        (need to bypass output ram)
                             //   RDW: New data for Read-During-Write
         .IFILE  (""     ))  // text: initializtion file, optional
mpram_inst ( .clk  (clk  ),  // clock
             .WEnb (WEnb ),  // write enable for each writing port               
                             //   - input : [nWPORTS-1:0            ]
             .WAddr(WAddr),  // write addresses - packed from nWPORTS write ports
                             //   - input : [`log2(MEMD)*nWPORTS-1:0]
             .WData(WData),  // write data      - packed from nRPORTS read  ports
                             //   - output: [DATAW      *nWPORTS-1:0]
             .RAddr(RAddr),  // read  addresses - packed from nRPORTS read  ports
                             //   - input : [`log2(MEMD)*nRPORTS-1:0]
             .RData(RData)); // read  data      - packed from nRPORTS read  ports
                             //   - output: [DATAW      *nRPORTS-1:0]
```