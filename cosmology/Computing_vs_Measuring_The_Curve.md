---
title: Computing versus Measuring the Curve
kind: note
publish: false
---

# Computing versus Measuring the Curve

A working note answering one objection precisely: that geodetic surveying *computes* with a curve rather than *measuring* one — that the curvature is an assumption plugged into formulas, never an observation. The distinction is real and worth holding. The answer is that the curvature is measured first, by a procedure whose result could have come back flat, and only then used in the survey formulas. Below: how it is measured, how the large-area method uses it, and how the leveling correction is checked against a measurement that assumes nothing about the earth's shape.

## Part 1 — How the curve is measured: arc measurement

This is the procedure that returns the earth's radius R as an observed number. It is two measurements divided by each other.

1. Choose two stations roughly north–south, as far apart as practical (hundreds of kilometres for precision).
2. Measure the ground distance S between them — by triangulation carried from a directly measured base line (Breed-Hosmer, *Higher Surveying*, Ch. I; base-line measurement and its corrections, Arts. 22–27).
3. At each station, measure the astronomical latitude: the angle between the local plumb line and a star at culmination (or the sun, corrected for its finite distance). Call these φ₁ and φ₂.
4. Take the measured difference Δφ = φ₂ − φ₁. Because a star's rays arrive parallel at both stations — stars are far, which stellar parallax independently establishes — Δφ is the angle between the two local plumb lines, i.e. how much "down" has rotated between the two points.
5. Compute R = S / Δφ, with Δφ in radians.

The result is empirical, and the experiment could have returned flat. On a flat earth the plumb line points the same direction everywhere: Δφ = 0 for any S, and R is infinite. The measured Δφ is not zero — about one degree per 111 km — so R comes out near 6,371 km. A distance and an angle, divided, yield the curvature. This was done by Eratosthenes, then with instruments by the French, Lapland, Peru, and Great Indian arcs and the Struve arc; the difference between the Lapland and Peru values measured the earth's *oblateness*, a finer result still.

Robustness against the "near light source" alternative: every star, regardless of which one, returns the same Δφ for the same two stations. That is what parallel rays over a rotated plumb line give. A single near source causing the angle by perspective would give different stations different values. The agreement across all stars is itself a measurement that the rays are parallel and the plumb line turned.

## Part 2 — The large-area method uses the measured R

Geodetic triangulation, condensed:

1. Measure one base line to ~1 ppm (invar, with standardization, temperature, tension, sag, and slope corrections).
2. Extend it through a base net to a full-length side.
3. Build a net of well-conditioned triangles over intervisible stations.
4. Measure every angle with a theodolite, in both telescope faces and many repetitions, to cancel instrument error (first-order triangle misclosure under ~1″).
5. Fix orientation and position astronomically at Laplace stations (latitude, longitude, azimuth — Breed-Hosmer Art. 133, Laplace's formula).
6. Reduce each triangle to the reference spheroid: compute its spherical excess ε = area / R² and apply Legendre's theorem (subtract ε/3 from each angle), or solve directly by spherical trigonometry (Breed-Hosmer, table for computing spherical excess, p. 616).
7. Propagate side lengths from the base by the law of sines.
8. Carry geodetic positions station to station by the ellipsoidal direct problem, starting from the datum origin.
9. Adjust the redundant net by least squares.
10. Measure a base of verification far across the net and compare it to the triangulated length (first-order agreement ~1 part in 100,000).

The measured R enters at steps 6–8 — the trigonometry that turns angles into sides and positions is spheroidal. Put R = ∞ (a flat earth) into the same raw observations and two measured checks fail: the triangle angle-sums, observed above 180°, will not reconcile, and the verification base will not match. The flat computation breaks its own checks, and those checks are measurements.

## Part 3 — The leveling correction: derived from measured R, confirmed without assuming it

Curvature drop from geometry: an instrument's horizontal sight is tangent to the level surface; at distance D the surface has fallen by

    c = √(R² + D²) − R ≈ D² / (2R),

which with the measured R (3,959 mi) gives c = 0.667 D² feet (D in miles) — Davis-Foote's figure. Refraction bends the sight into a downward arc of radius about 7R, lifting the target by roughly c/7, so the combined correction is (c − r) ≈ 0.574 D² feet (Breed-Hosmer, Art. 14).

The check that this is not circular is reciprocal leveling (Breed-Hosmer, reciprocal observations). Observe the height difference A→B from A and B→A from B. Each carries the same (c − r). Their mean cancels (c − r) exactly and yields the true height difference with no curvature assumed anywhere; their semi-difference *is* (c − r) — a direct measurement of the correction. The measured (c − r) matches the geometric 0.574 D². The correction is therefore tied to an observation that presupposes nothing about the earth's figure.

## The order of operations

Measure R by arc measurement — the rotation of the plumb line per unit ground distance, an angle that could read zero and does not. Then use R in the survey formulas. The formulas compute; they compute with a measured input, as every formula does. The curve is re-measured independently by the triangle excess and by reciprocal leveling, both of which return the same figure. The one place the curve is genuinely computed and applied rather than read — the short leveling shot — still draws on a measured R and is itself checked by a direct reciprocal measurement. Computing sits downstream of measuring here, not in place of it.
