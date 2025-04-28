# CMOS Inverter
## Setup
- CMOS Inverter driving a capacitor
- Bifurcation parameter: $(W/L)_n$

## Mathematical formulation
KCL at the output node:
$$C \frac{dV_{out}}{dt} = I_p(V_{out}) - I_n(V_{out})$$

where
- $I_p(V_{out})$ is PMOS current as a function of output voltage
- $I_n(V_{out})$ is NMOS current as a function of output voltage

Given the bifurcation parameter is based on device sizing, the currents of the devices can be written as:
$$I_n(V_{out}) = k_n (W/L)_n f_n(V_{out})$$
$$I_p(V_{out}) = k_p (W/L)_p f_p(V_{out})$$

where
- $k_n, k_p$ are technology constants
- $f_n, f_p$ are voltage-dependent functions based on region of operation (triode, saturation)

Thus the KCL equation becomes:
$$C \frac{dV_{out}}{dt} = k_p (W/L)_p f_p(V_{out}) - k_n (W/L)_n f_n(V_{out})$$

Fixed points occur when $\dot{V}_{out}=0$, so
$$k_p (W/L)_p f_p(V^*_{out}) = k_n (W/L)_n f_n(V^*_{out})$$

## Simulation Setup
The values for width and length of NMOS devices considered are:
| Device | $W$     | $L$ | $(W/L)$    |
|--------|---------|-----|------------| 
| NMOS   | [0.5,4] | 2   | [0.25,2]   |
| PMOS   | 2       | 2   | 1          |

Since a DC operating point analysis assumes $\frac{dV_{\text{out}}}{dt} = 0$, the resulting plot captures the set of fixed points $V_{\text{out}}^*$ corresponding to each $W_n$.

To determine the local stability of the fixed points, the derivative
$$
f(V_{\text{out}}) = \frac{d}{dV_{\text{out}}} \left( I_p(V_{\text{out}}) - I_n(V_{\text{out}}) \right)
$$
was computed.

It was observed that $f(V_{\text{out}}) < 0$ for all tested values of $W_n$. This condition implies that all fixed points are locally asymptotically stable. Physically, this means that any small perturbation to $V_{\text{out}}$ results in corrective currents that drive the system back to the equilibrium point.