# eFPGA: RTL-to-GDS with SKY130
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Introdution
This repo experiments an implementation of an FPGA from RTL to GDS with open Skywater-130 PDK.
The design RTL was generated by [FABulous framework](https://github.com/FPGA-Research-Manchester/FABulous).
The fabric consists of 1440 LUT4s (180x CLBs) and 180 LUT5s (45x RegFiles) with dual ported memory blocks for register files and FIFOs. An embedded UART for configurations and CPU_IO interface (e.g. to RISC-V core) were also implemented in this version.

<p align="center">
  <img width="400" height="400" src="https://uc5a0ddeae1401df0858edbfa978.dl-eu.dropboxusercontent.com/cd/0/inline/BNeXJRvnGslMO0QQZg5d53bGQhA0lXcYBtSUupgGoR4kivyWpEx3avxc76y60pa-TqxisBF_kCCi0raCs5F6GkmpPq08qdq68j8Um1gcKDvRJJVzmvp8iTgS51-E2HUF4kdtStP03dwYIGxjK5sKxOJg/file#">
</p>

### Note
Due to the [issue of routing](https://github.com/FPGA-Research-Manchester/FABulous-SKY130) with the Openlane flow, this version was using Cadence Innovus for physical implementations. The Yosys was used to synthesize the design RTL. 

## Directory Organization
```bash
UoM_eFPGA
├── common
│   ├── GDS
│   │   ├── CPU_IO.gds
│   │   ├── eFPGA_top.gds
│   │   ├── LUT4AB.gds
│   │   ├── N_term_single2.gds
│   │   ├── N_term_single.gds
│   │   ├── RegFile.gds
│   │   ├── sky130_ef_io.gds
│   │   ├── sky130_fd_io.gds
│   │   ├── sky130_fd_sc_hd.gds
│   │   ├── S_term_single2.gds
│   │   ├── S_term_single.gds
│   │   └── W_IO.gds
│   ├── LEFfile
│   │   ├── CPU_IO.lef
│   │   ├── eFPGA_top.lef
│   │   ├── LUT4AB.lef
│   │   ├── N_term_single2.lef
│   │   ├── N_term_single.lef
│   │   ├── RegFile.lef
│   │   ├── sky130_ef_io.lef
│   │   ├── sky130_fd_io.lef
│   │   ├── sky130_fd_sc_hd.lef
│   │   ├── sky130_fd_sc_hd.tlef
│   │   ├── S_term_single2.lef
│   │   ├── S_term_single.lef
│   │   └── W_IO.lef
│   ├── MAP
│   │   └── sky130_lefpin.map
│   ├── MMMC
│   │   ├── UoM_eFPGA_mmmc_TClib.view
│   │   └── UoM_eFPGA_mmmc.view
│   ├── SCRIPTS
│   │   ├── impl_commands.tcl
│   │   ├── stream_gds.tcl
│   │   └── write_leflib.tcl
│   ├── SDC
│   │   ├── pnr
│   │   │   ├── func.ideal.bc.tcl
│   │   │   ├── func.ideal.wc.tcl
│   │   │   └── func.prop.tcl
│   │   └── synthesis
│   │       └── eFPGA_top.sdc
│   ├── SRC
│   │   ├── UoM_eFPGA.io
│   │   └── UoM_eFPGA.v
│   └── TIMING
│       ├── CPU_IO.lib
│       ├── eFPGA_top.lib
│       ├── LUT4AB.lib
│       ├── N_term_single2.lib
│       ├── N_term_single.lib
│       ├── RegFile.lib
│       ├── sky130_fd_sc_hd__ff_n40C_1v95.lib
│       ├── sky130_fd_sc_hd__ss_100C_1v60.lib
│       ├── sky130_fd_sc_hd__tt_025C_1v80.lib
│       ├── S_term_single2.lib
│       ├── S_term_single.lib
│       └── W_IO.lib
├── OUTPUT
└── SAVED
```

## Todo:
- Update CLB, RegFile blocks
- Provide DSP, BRAM blocks
- Provide custom cells (e.g., multiplexers)
- Implement the fabric using the Openane flow

