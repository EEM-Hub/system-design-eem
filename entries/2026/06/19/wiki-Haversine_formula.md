---
source: sources/wiki-Haversine_formula.md
source_url: https://en.wikipedia.org/wiki/Haversine_formula
---

## Haversine Formula for Great-Circle Distance

The haversine formula computes the great-circle distance between two points on a sphere given their latitudes and longitudes. It is a special case of the law of haversines from spherical trigonometry. Historically important in maritime navigation, the formula uses the haversine function (half the versine) to avoid numerical precision issues that affect the equivalent spherical law of cosines when points are close together. The term "haversine" was coined by James Inman in 1835 as a contraction of "half-versed sine."

## Key Concepts

- **Haversine function**: hav(θ) = sin²(θ/2) = (1 − cos θ) / 2
- **Great-circle distance**: the shortest distance between two points on a sphere's surface, measured along the surface (d = r · θ, where θ is the central angle in radians)
- **Core formula**: hav(θ) = hav(Δφ) + cos(φ₁) · cos(φ₂) · hav(Δλ), where φ = latitude, λ = longitude
- **Solving for θ**: θ = 2 · arcsin(√(hav θ))
- **Numerical advantage over spherical law of cosines**: when two points are very close, the cosine formula yields cos(d/R) ≈ 1.0, causing floating-point precision loss; the haversine form uses sines and avoids this
- **Numerical weakness**: near-antipodal points (h approaching 1) can cause floating-point errors, but the resulting distance error is small relative to the large distance involved
- **Earth approximation limitation**: Earth is an oblate spheroid, not a perfect sphere; Earth's radius varies from ~6,356.752 km (poles) to ~6,378.137 km (equator); the haversine formula cannot guarantee better than ~0.5% accuracy
- **Law of haversines** (general form for spherical triangles): hav(c) = hav(a − b) + sin(a) · sin(b) · hav(C), where a, b, c are arc-length sides and C is the angle opposite side c
- **The navigation formula is a special case** where one vertex is the north pole, reducing co-latitudes to cos(φ) terms

## Commands and Syntax

**Expanded computation (in any programming language):**
```
Δφ = φ₂ − φ₁
Δλ = λ₂ − λ₁
a  = sin²(Δφ/2) + cos(φ₁) · cos(φ₂) · sin²(Δλ/2)
θ  = 2 · arcsin(√a)
d  = R · θ
```
Where R is the Earth's mean radius (~6,371.2 km), and all angles are in radians.

**Worked example** (White House to Eiffel Tower):
- White House: 38.898° N, 77.037° W
- Eiffel Tower: 48.858° N, 2.294° E
- Δφ = 9.960°, Δλ = 79.331°
- hav(θ) ≈ 0.21616, θ ≈ 55.411° ≈ 0.96710 rad
- d ≈ 0.96710 × 6371.2 km ≈ 6,161.6 km (vs. 6,177.45 km by ellipsoidal geodesic)

## Relationships

- **Spherical law of cosines**: theoretically equivalent but numerically inferior for small distances; the haversine form is derived from it via the identity cos(θ) = 1 − 2·hav(θ)
- **Vincenty's formulae**: more accurate for Earth distance calculations because they model the Earth as an ellipsoid rather than a sphere
- **Versine / haversine function**: hav = versine/2; historical tables eliminated division/multiplication by 2 for manual computation
- **Spherical trigonometry**: the law of haversines generalizes the distance formula to arbitrary spherical triangles
- **Geographical distance**: a broader topic covering multiple methods (haversine, Vincenty, Karney) with increasing accuracy
- **Sight reduction**: celestial navigation procedure that uses similar spherical geometry
- **Proof technique**: derived by converting lat/lon to Cartesian coordinates on a unit sphere, rotating to simplify one longitude to zero, then computing the dot product

## Exam-Relevant Points

- The haversine formula assumes a **perfect sphere** — on Earth it introduces up to ~0.5% error due to Earth's oblate shape
- **Numerical precision**: haversine is preferred over the spherical law of cosines for **nearby points**; neither handles **antipodal points** perfectly
- The formula requires all angles in **radians** for the final distance calculation (d = R · θ)
- **Earth's mean radius** commonly used: ~6,371 km
- The formula computes the **shortest surface path** (great-circle distance), not a straight-line (Euclidean) distance through the sphere
- For higher accuracy on Earth, use **Vincenty's formulae** (ellipsoidal model)
- The relationship hav(θ) = sin²(θ/2) is the definition that makes the formula work — know this identity
- The law of haversines for spherical triangles: hav(c) = hav(a−b) + sin(a)·sin(b)·hav(C) — the navigation formula is the special case where one vertex is the pole
