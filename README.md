# INV_ASAP7nm
INverter Layout with ASAP7nm Finfet Tech Lib



Aim is to examine the layout of a typical CMOS standard cell that includes both n-type and p-type finFETs. Many characteristics of traditional planar CMOS geometry are relevant to nonplanar finFET technology. A significant shift from traditional CMOS layout is that the transistor width (W) is no longer a variable in the design process.

The nonplanar ﬁnFET exhibits the same qualitative I DS dependence on V GS and V DS
as did the traditional planar MOSFET, under gradual-channel conditions, provided
that the planar width W is replaced by the nonplanar effective width W eff.

      W_eff = (2h_fin + t_fin)

While its I-V characteristics exhibit the same first-order behavior as planar MOSFETs, the nonplanar finFET is fundamentally more resistant to short-channel effects (SCEs). If the corner radius is not precisely managed during fabrication, a tri-gate finFET may display two threshold voltages. One technique to avoid this problem is to fabricate a thick dielectric layer termed as hard mask—atop the ﬁn. The hard-masked device effectively has two gates, both connected electrically, with one con-
trolling each side of the ﬁn. The BSIM-CMG model includes a SPICE parameter named TMASK. It is used to specify the thickness of the hard mask. Setting TMASK ¼ 0 indicatesthat there is no hard mask;
