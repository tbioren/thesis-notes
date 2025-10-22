## Span-4 and Span-12

They are arranged like a grid. Below are vertical and horizontal examples:

![[sp4h.svg]]
![[sp4v.svg]]

The wires are addressed by their relationship to the cell you are in. The table shows how this works.

**Horizontal:**

| Cell Coordinates | sp4_h_l_* wire name | sp4_h_r_* wire name |
| ---------------- | ------------------- | ------------------- |
| x, y             | –                   | sp4_h_r_0           |
| x+1, y           | sp4_h_l_0           | sp4_h_r_13          |
| x+2, y           | sp4_h_l_13          | sp4_h_r_24          |
| x+3, y           | sp4_h_l_24          | sp4_h_r_37          |
| x+4, y           | sp4_h_l_37          | –                   |

**Vertical:**

| Cell Coordinates | sp4_v_t_* wire name | sp4_v_b_* wire name | sp4_r_v_b_* wire name |
| ---------------- | ------------------- | ------------------- | --------------------- |
| x, y             | –                   | sp4_v_b_0           | –                     |
| x, y-1           | sp4_v_t_0           | sp4_v_b_13          | –                     |
| x, y-2           | sp4_v_t_13          | sp4_v_b_24          | –                     |
| x, y-3           | sp4_v_t_24          | sp4_v_b_37          | –                     |
| x, y-4           | sp4_v_t_37          | –                   | –                     |
| x-1, y           | –                   | –                   | sp4_r_v_b_0           |
| x-1, y-1         | –                   | –                   | sp4_r_v_b_13          |
| x-1, y-2         | –                   | –                   | sp4_r_v_b_24          |
| x-1, y-3         | –                   | –                   | sp4_r_v_b_37          |
