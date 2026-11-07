# CLAUDE.md — Project Context & Engineering Guidelines for `phase-ballast`

## 1. Project Overview
`phase-ballast` (**PhaseBallast**) is an R&D and product engineering repository for **marine phase-change thermal energy storage (TES) batteries**—storing latent heat (`55°C–75°C`) and latent cold (`-15°C` to `+7°C`) using solid $\leftrightarrow$ liquid phase transitions (paraffin wax, salt hydrates, bio-esters, and water/ice) for domestic hot water, cabin heating, overnight air conditioning, and refrigeration.

Primary reference document: [`pcm-thermal-ice-battery-guide.md`](pcm-thermal-ice-battery-guide.md).

---

## 2. Core Engineering Rules & Expansion Physics (Do Not Violate)

1. **Opposite Expansion Directions (Paraffin vs. Water):**
   * **Paraffin Wax & Fatty Acids expand by `+10% to +14%` upon MELTING** (solid $\rightarrow$ liquid) and shrink upon freezing (forming shrinkage voids). If hot heat-transfer fluid (`HTF`) melts a pocket of paraffin at the bottom/center of a tank while a frozen solid crust bridges the top, the trapped `+12%` liquid expansion creates hydraulic lock that ruptures tanks or crushes tubes.
   * **Water / Ice expands by `+9.0%` upon FREEZING** (liquid $\rightarrow$ solid). If an ice tank freezes from the outside walls or top surface inward, a solid ice dome traps liquid water in the core; as that core freezes last, hydraulic pressures exceed `100 MPa` and split metal welds.
   * **Positive-Temperature AC Alkanes/Esters (`n-tetradecane` at `+5.8°C`) contract (`-9%`) upon freezing**, avoiding ice-burst pressure while boosting chiller `COP` by `+35%`.

2. **Mandatory Expansion-Compensation Design Rules:**
   * Every tank, capsule, or heat-exchanger design in this repository **must** include at least one explicit volumetric expansion compensation mechanism that functions at **`0° to 45°` boat heel angles**:
     1. **Macro-Encapsulation in Compliant Polymer Cartridges (`HDPE`, `PP-R`, `PEX-a` tubes or dimpled plates with `12–14%` internal gas ullage):** Cartridges flex elastically (`<1 mm`) as PCM changes phase, displacing external unpressurized `Propylene Glycol + Water` HTF into an external hydronic EPDM bladder expansion tank.
     2. **Expanded Graphite (`15–20 wt%`) + Paraffin (`80–85 wt%`) Shape-Stabilized Matrix (`EG/PCM`):** Absorbs the `+12%` melt expansion inside `10–40 µm` capillary graphite pores (`10–12%` residual void fraction), prevents free-liquid sloshing at sea, and raises thermal conductivity from `0.20 W/m·K` to **`5.0–12.0 W/m·K`**.
     3. **Closed-Cell Compressible Elastomer Cores (`12–15%` volume fraction):**
        * Use **closed-cell `EPDM` or `XLPE` foam** for **water/ice and salt brines (`-20°C to +35°C`)**.
        * **Never use standard EPDM or Neoprene inside hot liquid paraffin wax** (hydrocarbons swell and dissolve EPDM!). Always specify **closed-cell Fluorosilicone (`FVMQ`)**, **Nitrile (`NBR` / `Buna-N`) closed-cell sponge**, or **sealed corrugated `316L` stainless bellows** for hydrocarbon waxes.
     4. **Vertical "Thermal Chimney" Fin for Bulk Paraffin Tanks:** Any bulk shell-and-tube paraffin tank must route the hot HTF inlet pipe vertically down through the top `15%` gas headspace first with full-height longitudinal aluminum/copper fins so a molten pressure-relief channel opens to the top free surface *before* bulk melting occurs at the bottom.
     5. **Electronic Ice-Bridge Prevention for Pure Water Ice-on-Coil:** Always include an ice-thickness limit sensor (conductivity or NTC probe at `15–20 mm` radial standoff) so adjacent ice cylinders never merge into a solid monolithic block (`maintain ≥25%–30% free liquid water fraction`).

3. **Chemical & Fire Safety Constraints:**
   * Keep hot paraffin/fatty-acid heat-source loops **`≤85°C–90°C`** (well below the `~200°C–220°C` flash point of `C24–C30` paraffins) and include an independent `95°C` thermal cutoff switch on any electrical dump heating element.
   * For **Sodium Acetate Trihydrate (`SAT`, `58°C`, `264 kJ/kg`, `380 kJ/L`)**, always specify `1–2 wt%` nucleating agent (`disodium hydrogen phosphate` `DSP`) to prevent supercooling and `1–2 wt%` thickener (`CMC` or `xanthan gum`) to prevent incongruent phase segregation.
   * All circulating marine HTF loops must use **non-toxic USP food-grade Propylene Glycol + Deionized Water** (never toxic automotive ethylene glycol near domestic hot water heat exchangers).
