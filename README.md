# INV_ASAP7nm
Inverter Layout with ASAP7nm Finfet Tech Lib.

Many characteristics of traditional planar CMOS geometry are relevant to nonplanar finFET technology. A significant shift from traditional CMOS layout is that the transistor width (W) is no longer a variable in the design process.

The nonplanar FinFET exhibits the same qualitative dependence of I_DS on V_GS and V_DS as the traditional planar MOSFET under gradual-channel conditions, with the planar width W replaced by the effective width W_eff of the nonplanar structure.

      W_eff = (2h_fin + t_fin)

Although the I-V characteristics of the nonplanar FinFET show the same first-order behavior as planar MOSFETs, it is inherently more resistant to short-channel effects (SCEs). However, if the corner radius is not carefully controlled during fabrication, a tri-gate FinFET may exhibit two distinct threshold voltages. One approach to prevent this issue is to add a thick dielectric layer, known as a hard mask, on top of the fin. In a hard-masked device, there are effectively two gates, electrically connected, with each controlling one side of the fin. The BSIM-CMG model includes a SPICE parameter called TMASK, which specifies the hard mask thickness. Setting TMASK to 0 indicates that there is no hard mask.


The manufacturing process of FinFET technology is divided into three key stages: front-end-of-line (FEOL), middle-of-line (MOL), and back-end-of-line (BEOL). 

The FEOL stage is dedicated to fabricating the foundational elements, such as wells and transistors, encompassing critical features like the active regions, fins, gates, and diffusion areas.

The BEOL stage, on the other hand, focuses on creating electrical connections through a series of metal layers, starting from metal 1 (M1) up to the top metal layer (M9), facilitating both local and global routing within the cell. 

The MOL stage bridges the gap between FEOL and BEOL. For example, the source-drain trench (SDT) layer connects the active regions to the local interconnect source-drain (LISD) layer, which subsequently links the source and drain terminals of the transistors. 

The LISD is stacked above the SDT within the MOL structure, while the local interconnect gate (LIG) layer provides connections to the gate terminals. 

The V0 layer then links the LIG and LISD layers to the BEOL layers above, completing the routing infrastructure.

## File structure: 

    ASAP7.lyt : technology and connections description
    ASAP7.lyp : layers color and shape description
    drc/drc_ASAP7.lydrc : DRC script
    finalinv.gds : Inverter layout 

## Setup Klayout with ASAP7: 

Install Klayout from [here](https://www.klayout.de/build.html). Make sure you install >0.28 version and have all the dependencies sorted.

      git clone https://github.com/deepsita/INV_ASAP7nm.git

Open Klayout in edit mode 

      klayout -e

[Tools]-[Manage Technologies]

      Add a new technology by hovering to + in the bottom. 

      Add the .lyt, .lyp and drc folders to your .klayout directory. 

Check if technology is selected and loaded properly by checking the T icon in the task ribbon of GUI. 

You can select the ASAP7 once you create the technology. 

Start a New layout from File Menu. 

If you see the layoers are not properly loaded, You can go to File, Load Layer Properties and load .lyp. 

## Draw Inverter Layout

Following are few rules that I referred from ASU reference.

Gate width = 0.02um

Gate pitch = 0.054um

Fin width = 0.007um

Fin pitch = 0.027um

Cell height = 0.288um

SDT width = 0.024um

Minimum width M1, M2, M3 = 0.018um

V0, V1, V2 = 0.018um x 0.018um

Step 1: **Gate Drawing** - width of 0.02u and a height of 0.288u. Two dummy gates on each side. distance between gates 0.034um, pitch=0.054umm

Step 2: **Fins** -- width 0.007um heigh --0.019um total of 9 fins and distance between each fin is 0.02um and fin pitch is 0.027um.

Step 3: **boundary layer**

Step 4: **well drawing** 0.162um x 0.144um

Step 5: **Gcut draawing** It is drawn at the center of dummy gates (0.054um x 0.044um) and also at the top and bo om (0.162um x 0.037um). Bottom GCut layer is 0.006um below the x-axis and at the top its 0.006 above the BOUNDARY layer.

Step 6: **Active drawing** for pfet and nfet (0.07um x 0.081um). W p = W n = 0.081um. On left and right, distance between the dummy gate and Active layer is 0.009um. On top and bottom, distance between the GCut layer and Active layer is 0.005um.

Step 7: Draw **SDT drawing** on Ac ve (0.024 um x 0.081 um). The distance between Gate and SDT is 0.005um. SDT is drawn on Ac ve layer wherever connec ons are to be made. If a source or drain has no connectons, then SDT layer should not be drawn.

Step 8: Draw **LISD drawing** on top on SDT drawing, wherever VDD and GND connec ons are to be made, extend the LISD layer above the Active layer by 0.027um.

Step 9 : Draw **LIG drawing** for connecting the LISD layer to VDD and GND (0.162um x 0.016um). One for gate connection (0.022um x 0.024um). The distance GCut layer and LIG layer is 0.014um LIG for gate connection: (0.022um x 0.024um). Distance from GCut (left and right): 0.016um, Distance from Active (top and bottom): 0.015um

Step 10: Draw V0 drawing for the all gates, nets and VDD, GND place V0 on LIG layer. V0: 0.018um x 0.018um.

Step 11: Draw M1 to connect the nets and for VDD and GND

Step 12: Draw Pselect on top on pfet and Nselect on top of nfet (0.162um x 0.135um).

Step 13: VDD and GND are brought to M2.Input and output pins are brought up to M3. For VDD and GND, draw M2 on top of M1, place V1 (0.018um x 0.018um) to connect M1 to M2

Step 14: Input and output pins should be brought up to M3,Place M2 and V1 (0.018um x 0.018um) on top of M1.Now place M3 and V2 (0.018um x 0.018um) on top of M2.

![INVLayout](https://github.com/user-attachments/assets/e16666f9-c5d1-470a-ae33-97a61123fda8)


References: 
https://github.com/laurentc2/ASAP7_for_KLayout

