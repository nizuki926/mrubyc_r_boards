# mrubyc_r_boards
mruby/c sample program for Renesas boards

# Usage (Windows)
## Install GCC for Renesas RX
- Please install GCC for Renesas RX.

## Rename hal folder
- Open the `src` folder.
- Please rename the hal folder of the target microcomputer.
- For RX65N, rename `hal_rx65N` to `hal`.

## Rename board folder
- Open the `sample_c` folder.
- Please rename the board folder of the target board.
- For the Target Board for RX65N, rename `board_tb_rx65n` to `board`.

## Build the mruby/c library and sample program
- Execute `RX-ELF Toolchain`.
- Move to top folder.
- Execute the `make all` command.
- The `mrubyc.mot` will be generated in the `board` folder.

## Write the sample program to the target microcomputer
- For Target Board for RX Family, It is necessary to write the sample program with `Renesas Flash Programmer`.
- After writing, the `Mode Pins at Disconnection` must be set to `Reset Pin as Hi-Z` to execute the program.