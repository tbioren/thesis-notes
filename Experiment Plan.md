### Next Steps

1. Prove the ASC files are the same for every Yosys -> nextpnr run.
2. Prove the bitstream layout in the iCE40 Layout Viewer is the same as the graph representation. Document every step from graph to layout.
3. Figure out IceStorm timing simulation tool and determine if it's usable for determining fitness.
4. Make an evolution program.
5. Evolve a 1-bit adder.
## Stages

**CGP $\rightarrow$ HDL $\rightarrow$ Yosys $\rightarrow$ nextpnr $\rightarrow$ bitstream**

### CGP Stage

Every node in the graph represents a logic cell. It has up to 4 inputs and 1 output. The 1 output can go to multiple other nodes' inputs.

Eventually, I want to switch to nodes representing tiles and having subgraphs for the LUTs.

#### Genotype Format
### Genotype Representation

- The inputs should be relative coordinates.
- There should be no x and y coordinates because we'll know them by its index in the array.
- It should be easy to scale up/down.

**Array Representation:**

```C
[LUT_behavior, input0_x_offset, input0_y_offset, input1_x_offset, input1_y_offset, input2_x_offset, input2_y_offset, input3_x_offset, input3_y_offset]
```

**Scaled to 1 bit adder:**

```C
// Same as the array representation but scaled to smaller numbers for fewer LUTs.
0000 00 00 00 00 00 00 00 00
```

**C Struct Representation:**

```C
struct node {
    uint8_t x_coordinate;
    uint8_t y_coordinate;
    int16_t LUT_behavior;
    uint8_t input0_x;
    uint8_t input0_y;
    uint8_t input1_x;
    uint8_t input1_y;
    uint8_t input2_x;
    uint8_t input2_y;
    uint8_t input3_x;
    uint8_t input3_y;
};
```

### HDL Stage

The code directly makes Verilog out of the nodes. [[Yosys]] tries to optimize the Verilog unless you include `(* keep, dont_touch *)` before your module blocks. You can also specify LUT locations with `(* LOC = "X0/Y0" *)`.

#### Verilog Syntax

**Module:**
```verilog
module cgp_module (
    (* keep *) input in0, in1, in2, in3, in4, in5, in6, in7, in8, in9,
    (* keep *) output out0, out1, out2, out3, out4, out5, out6, out7, out8, out9);

    (* keep *) wire x0_y0, x1_y0, x2_y0,...;
    ```

The wires are all outputs of LUTs that don't go straight to the output tiles.

**Nodes:**
```verilog
(* keep, dont_touch *)
(* LOC = "X0/Y0" *)
SB_LUT4 #(
    .LUT_INIT(16'b0110011101101111)
) lut_0_0 (
    .O(x0_y0),
    .I0(in0),
    .I1(in2),
    .I2(in3),
    .I3(in0)
);
```

This is a "first layer" node because it only has inputs.