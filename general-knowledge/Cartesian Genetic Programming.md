## What It Is

Cartesian Genetic Programming (CGP) is a way of representing a program structure as a digraph. Each node represents an operation (I think that's called a phenotype **CONFIRM**).

![[CGP_Example.png]]

## Ways to Implement

- [hal-cgp](https://github.com/Happy-Algorithms-League/hal-cgp]) seems like it's a well-supported CGP python repository.
- [CGP-Library](https://github.com/AndrewJamesTurner/CGP-Library) is for C.

## Notes

- The nodes in the CGP graph can seem to connect to any other node as long as they're n columns behind them. I'm worried about the limits of FPGA routing because you can't explicitly connect LUTs or logic tiles together like that. #question