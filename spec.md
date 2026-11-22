# Beam Designer

## Purpose
Shear, moment, and deflection diagrams for a beam, with separate checks
of bending stress and deflection for the specified loading.

## Inputs
- Simply supported or cantilever, and the span (ft)
- Uniform loads (kip/ft); no point loads
- A steel W-shape or a lumber size, with species and grade for lumber
- Additional safety factor, default 1.0 and minimum 1.0

## Material and member properties
- Define elastic modulus E, moment of inertia I, section modulus S, and
  allowable bending stress for each selectable material and member.
- Document the sources, units, and basis of these properties, including
  any adjustments used for lumber allowable bending stress.
- Use published allowable stresses consistently. The additional safety
  factor is an extra reduction of the allowable stress, not a second
  application of safety provisions already included in the source values.

## Calculations
- Reactions, shear, and moment from statics
- Deflection
- Bending stress fb = M/S, using the maximum absolute bending moment
- Bending stress limit = published allowable bending stress / additional
  safety factor; bending passes when the stress does not exceed this limit
- Deflection compared to L/360
- Apply the additional safety factor to the bending stress limit only;
  keep the deflection limit at L/360

## Outputs
- The beam with its loads, and the three diagrams
- Separate Bending PASS/FAIL and Deflection PASS/FAIL results
- Show the stress and deflection values alongside their respective limits
- Do not present an overall safety verdict; these results cover only the
  bending and deflection checks included in this app

## Look and feel
Clean and professional, with an example beam loaded when it opens.
Use the uniform-load-only validation example below for the initial beam,
without the mockup's point load.

## Input validation and recalculation
- Require finite numeric inputs, a span greater than zero, and an
  additional safety factor of at least 1.0.
- Reject any load positions or extents outside the beam if those fields
  are offered.
- Give invalid fields a red border and a short explanation next to the
  field; do not rely on color alone.
- Do not calculate while required inputs are invalid or missing.
- After an analysis input changes, mark existing results as needing
  recalculation until Calculate is pressed successfully.

## Validation
20 ft simply supported W12x26 with 1 kip/ft: M = 50.0 kip-ft,
deflection 0.609 in.

- Record the material properties and reference calculations used for
  each validation case in `02_validation/`.
- Check reactions, shear, moment, deflection, and diagram shapes for
  uniform loads on both simply supported and cantilever beams.
- Include an unloaded beam and partial-span uniform loading if that
  loading option is supported.
- Verify bending and deflection results below, at, and above their limits.
- Verify that increasing the additional safety factor lowers the bending
  stress limit without changing reactions, diagrams, or the L/360 limit.
- Check invalid and missing inputs, red field styling and error messages,
  and the need-to-recalculate state after an input changes.

## Out of scope
Point loads, continuous beams, buckling, shear-strength checks, and
connection design.


## Build the App in Five Testable Stages

### Summary

The current spec.md only says this is a single-file web app served from the top-level index.html; it does not describe the app’s purpose or calculations. Use this staged approach as a general development sequence, and fill in the app-specific fields and formulas once the specification defines them.

### Stages and Checks

1. Layout mockup — Create the page structure and visual styling in index.html, using placeholder values and controls. Add no real calculations.
   Check: Open the page locally and confirm the sections, labels, and controls are easy to see and use at desktop and phone widths.
2. Input behavior — Make the controls accept and display user input. Keep results as placeholders.
   Check: Enter, edit, and clear values; confirm the page responds as expected and handles empty or malformed input clearly.
3. Calculation logic — Implement the app’s specified calculations and connect them to the inputs.
   Check: Compare results against hand-calculated examples, including boundary values and invalid inputs.
4. Results and feedback — Show calculated outputs with appropriate formatting and useful validation or error messages.
   Check: Confirm outputs update when inputs change, are readable, and errors identify what needs fixing.
5. Polish and publish readiness — Refine layout and accessibility, then verify the single-file page works as a GitHub Pages entry point.
   Check: Test keyboard navigation, labels, responsive layout, and loading from the top-level index.html.

### Interfaces

Keep the app self-contained in the top-level index.html, as required by spec.md. The current specification defines no particular input, output, or calculation interface.

### Assumptions

- The app’s domain, input fields, formulas, and expected outputs are not specified yet.
- Each stage should be reviewed in the browser before beginning the next.
- No code has been written as part of this plan.
