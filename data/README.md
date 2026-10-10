# Numerical datasets

All files are whitespace-delimited plain text without headers. The files in `mesh/` are required inputs. Files in `reference/` are supplied exports retained for comparison and are not read automatically by the notebook.

## Mesh inputs

| Files | Columns | Meaning |
| --- | --- | --- |
| `mesh/wezly_N_2_L_100.dat`, `mesh/wezly_N_4_L_100.dat`, `mesh/wezly_N_6_L_100.dat` | `node_id x y` | One-based global node ID and coordinates in nanometres. |
| `mesh/nlg_N_2_L_100.dat`, `mesh/nlg_N_4_L_100.dat`, `mesh/nlg_N_6_L_100.dat` | `element_id local_node_id global_node_id` | One-based mapping from each element's nine local nodes to the global mesh. |

The supplied coordinates describe the reference square with side length $L=100\,\mathrm{nm}$. The notebook scales them for the domain-size study.

| $N$ | Node rows | Mapping rows | Elements |
| --- | ---: | ---: | ---: |
| 2 | 81 | 144 | 16 |
| 4 | 289 | 576 | 64 |
| 6 | 625 | 1296 | 144 |

## Matrix exports

| File | Columns | Matrix dimensions |
| --- | --- | --- |
| `reference/S_loc_N2_L100.dat` | `i j S_ij` | $9\times9$ local overlap matrix. |
| `reference/T_loc_N2_L100.dat` | `i j T_ij` | $9\times9$ local kinetic-energy matrix. |
| `reference/V_loc_N2_L100_element_11.dat` | `i j V_ij` | $9\times9$ local potential-energy matrix for element 11. |
| `reference/macierzeS_H_au.dat` | `i j S_ij H_ij` | $81\times81$ global overlap and Hamiltonian matrices, including the boundary modifications. |

Matrix-file indices start at **1**. Printed notebook DataFrame indices start at **0**. Numerical values use the atomic-unit conventions of the original calculations and should not be interpreted directly as meV.

Small differences are present between these exports and the notebook's saved matrix values. For example, the first overlap-matrix entry is approximately 3967.509069 in the export and 3967.849812 in the saved notebook output. The original export environment is unavailable, so these files are historical comparison data rather than exact regression-test fixtures.
