# ngspice_tutorials

## Analog circuit analysis 

1. DC operating point
2. DC Sweep
3. Transient analysis
4. Frequency analysis

To simulate we need .cir files

* or asterisk is used for comments 

## Simple common source amplifier using MOSFET

![image](https://user-images.githubusercontent.com/98731221/211197045-f12f8b77-68d7-4b06-a238-a11023b42977.png)


### DC Analysis
```
.include cmos_130nm.txt

******Netlist part*********
VDD net1 GND 1.5
RD net1 vout 10k
VG vin GND 0.6
** M1 Drain Gate Source Substrate
M1 vout vin GND GND NMOS W=1u L=130n

*****Analysis*******

.control

****DC Analysis*****
op
print @M1[id]
print @M1[gm]
print v(vout)

.endc
.end
```
## DC sweep

```
.include cmos_130nm.txt

******Netlist part*********
VDD net1 GND 1.5
RD net1 vout 10k
VG vin GND 0.6
** M1 Drain Gate Source Substrate
M1 vout vin GND GND NMOS W=1u L=130n

*****Analysis*******

.control

***DC Sweep***
dc VG 0 1.5 0.1
plot v(vout)

.endc
.end

```

## Transistor parameters 
```
.include cmos_130nm.txt

******Netlist part*********
VDD net1 GND 1.5
RD net1 vout 10k
VG vin GND 0.6
** M1 Drain Gate Source Substrate
M1 vout vin GND GND NMOS W=1u L=130n

*****Analysis*******

.control

***DC Sweep***
save all @M1[id]
dc VG 0 1.5 0.1
plot @M1[id]

.endc
.end

```
