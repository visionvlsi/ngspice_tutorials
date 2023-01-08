## Inverter

```
.include 130nm_bulk.pm.txt

.param supply=1.5

*** Netlist ***

VDD net1 GND supply
MN1 output input GND GND NMOS w=0.5u L=130n
MP1 output input net1 net1 PMOS w=1u L=130n
C1 output GND 0.1p
Vin input GND pulse(0 supply 0 0.5p 0.5p 0.1u 0.2u)
.tran 1p 0.4u
.control
run
plot v(output)
.endc
.end
```

## With input
```
.include 130nm_bulk.pm.txt

.param supply=1.5

*** Netlist ***

VDD net1 GND supply
MN1 output input GND GND NMOS w=0.5u L=130n
MP1 output input net1 net1 PMOS w=1u L=130n
C1 output GND 0.1p
Vin input GND pulse(0 supply 0 0.5p 0.5p 0.1u 0.2u)
.tran 1p 0.4u
.control
run
plot v(output) v(input)+2
.endc
.end
```
