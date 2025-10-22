## Important Considerations

- Yosys is deterministic
- I can add `(* keep,dont_touch *)` to Verilog blocks to stop from optimizing.

Example Verilog:

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

Command:
```bash
yosys -p "read_verilog -lib +/ice40/cells_sim.v; read_verilog cgp_module.v; hierarchy -top cgp_module; proc; flatten; write_json cgp_module.json"
```