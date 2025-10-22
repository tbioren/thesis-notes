```shell
yosys -p " read_verilog cgp_module.v; synth_ice40 -top cgp_module -json cgp_module.json -nocarry;"

nextpnr-ice40   --up5k --package sg48   --json cgp_module.json   --asc cgp_module.asc   --report cgp_module.rpt   --write cgp_module_placed.json   --debug
```

### Graph
![[Pasted image 20251014090428.png]] 

### Verilog
```verilog
module cgp_module (
    (* keep *) input in0, in1, in2, in3, in4, in5, in6, in7, in8, in9,
    (* keep *) output out0, out1, out2, out3, out4, out5, out6, out7, out8, out9);

    (* keep *) wire x0_y0, x1_y0, x2_y0, x0_y1, x1_y1, x2_y1, x0_y2, x1_y2, x2_y2, x0_y3, x1_y3, x2_y3;


    (* keep, dont_touch *)
    (* BEL = "X1/Y1/lc0" *)
    SB_LUT4 #(
        .LUT_INIT(16'b1001011100010101)
    ) lut_0_0 (
        .O(x0_y0),
        .I0(in0),
        .I1(in0),
        .I2(in2),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X2/Y1/lc0" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0001101000011101)
    ) lut_1_0 (
        .O(x1_y0),
        .I0(in3),
        .I1(in3),
        .I2(in0),
        .I3(in0)
    );

    (* keep, dont_touch *)
    (* BEL = "X3/Y1/lc0" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0100111110111001)
    ) lut_2_0 (
        .O(x2_y0),
        .I0(in0),
        .I1(1'b0),
        .I2(1'b0),
        .I3(in3)
    );

    (* keep, dont_touch *)
    (* BEL = "X4/Y1/lc0" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0101000001010001)
    ) lut_3_0 (
        .O(x3_y0),
        .I0(1'b0),
        .I1(x1_y3),
        .I2(1'b0),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X1/Y1/lc1" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0001111000000101)
    ) lut_0_1 (
        .O(x0_y1),
        .I0(in0),
        .I1(in3),
        .I2(1'b0),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X2/Y1/lc1" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0110110100101001)
    ) lut_1_1 (
        .O(x1_y1),
        .I0(in2),
        .I1(in3),
        .I2(in0),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X3/Y1/lc1" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0110101100010000)
    ) lut_2_1 (
        .O(x2_y1),
        .I0(1'b0),
        .I1(in0),
        .I2(in0),
        .I3(in0)
    );

    (* keep, dont_touch *)
    (* BEL = "X4/Y1/lc1" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0110010001001001)
    ) lut_3_1 (
        .O(x3_y1),
        .I0(in0),
        .I1(1'b0),
        .I2(x1_y0),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X1/Y1/lc2" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0100100101001100)
    ) lut_0_2 (
        .O(x0_y2),
        .I0(in3),
        .I1(1'b0),
        .I2(in3),
        .I3(in3)
    );

    (* keep, dont_touch *)
    (* BEL = "X2/Y1/lc2" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0011111110000001)
    ) lut_1_2 (
        .O(x1_y2),
        .I0(1'b0),
        .I1(in1),
        .I2(1'b0),
        .I3(in0)
    );

    (* keep, dont_touch *)
    (* BEL = "X3/Y1/lc2" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0010101110100111)
    ) lut_2_2 (
        .O(x2_y2),
        .I0(1'b0),
        .I1(in0),
        .I2(in0),
        .I3(in3)
    );

    (* keep, dont_touch *)
    (* BEL = "X4/Y1/lc2" *)
    SB_LUT4 #(
        .LUT_INIT(16'b1111101101000111)
    ) lut_3_2 (
        .O(x3_y2),
        .I0(1'b0),
        .I1(in0),
        .I2(in3),
        .I3(1'b0)
    );

    (* keep, dont_touch *)
    (* BEL = "X1/Y1/lc3" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0101100101111101)
    ) lut_0_3 (
        .O(x0_y3),
        .I0(1'b0),
        .I1(in0),
        .I2(in3),
        .I3(in0)
    );

    (* keep, dont_touch *)
    (* BEL = "X2/Y1/lc3" *)
    SB_LUT4 #(
        .LUT_INIT(16'b0110001000001000)
    ) lut_1_3 (
        .O(x1_y3),
        .I0(1'b0),
        .I1(in2),
        .I2(in3),
        .I3(in3)
    );

    (* keep, dont_touch *)
    (* BEL = "X3/Y1/lc3" *)
    SB_LUT4 #(
        .LUT_INIT(16'b1111000111111011)
    ) lut_2_3 (
        .O(x2_y3),
        .I0(1'b0),
        .I1(in3),
        .I2(in2),
        .I3(in3)
    );

    (* keep, dont_touch *)
    (* BEL = "X4/Y1/lc3" *)
    SB_LUT4 #(
        .LUT_INIT(16'b1001110101111000)
    ) lut_3_3 (
        .O(x3_y3),
        .I0(1'b0),
        .I1(in3),
        .I2(1'b0),
        .I3(x1_y0)
    );

endmodule
```

### Layout

![[Pasted image 20251014090406.png]]