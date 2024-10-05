# INV_ASAP7nm
INverter Layout with ASAP7nm Finfet Tech Lib



Aim is to examine the layout of a typical CMOS standard cell that includes both n-type and p-type finFETs. Many characteristics of traditional planar CMOS geometry are relevant to nonplanar finFET technology. A significant shift from traditional CMOS layout is that the transistor width (W) is no longer a variable in the design process.

The nonplanar ﬁnFET exhibits the same qualitative I DS dependence on V GS and V DS
as did the traditional planar MOSFET, under gradual-channel conditions, provided
that the planar width W is replaced by the nonplanar effective width W eff.

      W_eff = (2h_fin + t_fin)

While its I-V characteristics exhibit the same first-order behavior as planar MOSFETs, the nonplanar finFET is fundamentally more resistant to short-channel effects (SCEs). If the corner radius is not precisely managed during fabrication, a tri-gate finFET may display two threshold voltages. One technique to avoid this problem is to fabricate a thick dielectric layer termed as hard mask—atop the ﬁn. The hard-masked device effectively has two gates, both connected electrically, with one con-
trolling each side of the ﬁn. The BSIM-CMG model includes a SPICE parameter named TMASK. It is used to specify the thickness of the hard mask. Setting TMASK ¼ 0 indicatesthat there is no hard mask;


![Screenshot from 2024-10-05 23-02-49](https://github.com/user-attachments/assets/5cd3da25-4d2c-4bf5-a5a8-d2107033ee37)

![Screenshot from 2024-10-05 23-06-38](https://github.com/user-attachments/assets/dbe5d1fb-203a-4421-aa83-45456be808df)

The manufacturing process for FinFET technologies is categorized into three stages: front-end-of-line (FEOL), middle-of-line (MOL), and back-end-of-line (BEOL). The FEOL stage focuses on creating wells and transistors, including key components like the active region, fins, gate, and diffusions. The BEOL stage involves establishing contacts through the via layer and the metallic layers, ranging from metal 1 (M1) to the top metal (M9), facilitating short connections and overall cell routing. The transition from FEOL to BEOL occurs in the MOL stage. For instance, the source-drain trench (SDT) layer connects the active area to the local interconnect source-drain (LISD) layer, which in turn links the source and drain terminals of transistors. The LISD layer is positioned above the SDT in the MOL stack, while the local interconnect gate (LIG) serves the gate terminal connections. The V0 layer is responsible for connecting the LIG and LISD to the BEOL layers.
