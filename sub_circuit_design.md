# Sub-circuit design

![image](https://user-images.githubusercontent.com/98731221/211210091-a10f1897-dcec-40d5-981e-4894ea902568.png)

![image](https://user-images.githubusercontent.com/98731221/211210262-9d9fb761-8cd8-44a2-8672-df8a08a6c18e.png)

```
.include 130nm_bulk.pm.txt
.param supply=1.5
*** Netlist ***
.subckt inv input output gnd
VDD net1 GND supply
MN1 output input GND GND NMOS w=0.5u L=130n
MP1 output input net1 net1 PMOS w=1u L=130n
.ends inv

Vin input GND pulse(0 supply 0 0.5p 0.5p 0.1u 0.2u)

x1 input net1 gnd inv
x2 net1 net2 gnd inv
x3 net2 net3 gnd inv
x4 net3 output gnd inv
c1 output gnd 0.1p
*******netlist ends*****
.tran 1p 0.4u
.control
run
plot v(output) v(input)+2
.endc
end
```
