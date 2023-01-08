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
# Calculate rise and delay
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
.measure tran T_rise trig v(output) val = 0.1*supply rise=1 targ v(output) val=0.9*supply rise=1
.measure tran T_fall trig v(output) val = 0.9*supply fall=1 targ v(output) val=0.1*supply fall=1
.control
run
plot v(output) v(input)+2
.endc
.end
```
