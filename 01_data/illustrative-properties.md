# Illustrative member properties

These values are examples for developing and checking the app. They are not a complete member-design catalog.

## Steel W12×26

- Strong-axis moment of inertia I = 204 in⁴ and elastic section modulus S = 33.4 in³, from the [AISC shape data reported by Quantum Steel Design](https://www.quantumsteeldesign.com/steel-tools/shapes/w12x26/).
- For the illustrative member, select ASTM A992: [AISC lists Fy = 50 ksi](https://www.aisc.org/aisc/solutions-center/engineering-faqs/1-mill-production-and-tolerances/) and reports a nominal [E = 29,000 ksi](https://www.aisc.org/globalassets/aisc/research-library/updating-standard-shape-material-properties-database-for-design-and-reliability.pdf).
- For illustration, the older AISC allowable-stress approach uses 0.66 Fy = 33.0 ksi for fully braced strong-axis bending of a compact member, as described in [AISC Steel Interchange](https://www.aisc.org/globalassets/modern-steel/steel-interchange/2014/012014_si.pdf). This is a historical simplified assumption, not a general current-code allowable bending stress. The app does not check bracing or buckling.

## Lumber example

- The [American Wood Council 2024 design values for joists and rafters](https://awc.org/wp-content/uploads/2023/11/AWC_DVJR2024_20231130_AWCWebsite.pdf) lists mixed Southern Pine, No. 2, 2×8 with E = 1,400,000 psi and bending value 1,065 psi for normal duration. The table's listed assumptions and footnotes must be applied to its use.
- For a dry surfaced 2×8, use [actual dimensions 1.5 in × 7.25 in](https://refmanual.com/charts/lumber-sizes/). Bent about its strong axis, I = bh³/12 = 47.63 in⁴ and S = bh²/6 = 13.14 in³. Actual dimensions and applicable adjustment factors must be confirmed for the selected member and conditions.
