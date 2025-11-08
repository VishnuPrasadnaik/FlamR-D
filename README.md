# Solution for R&D Assignment

The parametric curve equation with the extracted variables substituted is:


( t*cos(0.491) - exp(0.0214*abs(t))*sin(0.3*t)*sin(0.491) + 54.90,  42 + t*sin(0.491) + exp(0.0214*abs(t))*sin(0.3*t)*cos(0.491) )

where t is in the range 6 < t < 60, 0.491 radians ≈ 28.12 degrees (the value of θ), M = 0.0214, X = 54.90.

The Code is provided in the Flam.ipynb file of this repository.

The output of the code is as follows:
//
<img width="361" height="51" alt="image" src="https://github.com/user-attachments/assets/3547772f-f060-4fa1-9ee8-ab8f0fe8c1e9" />

"Mean L1 distance for the curve fitting: 25.24".

## Methodology:

### Steps Followed for Parameter Estimation
#### 1. Understanding the Problem and Data

Analyzed the parametric curve equations and identified the unknowns (θ, M, X).

Inspected the provided CSV of (x, y) points for t in [6, 60].

Applied variable ranges according to assignment (θ: 0-50°, M: -0.05-0.05, X: 0-100).

#### 2. Model Formulation

Converted θ from degrees to radians.

Implemented the parametric model in Python using the xy_data.csv provided in the assignment:

x(t) = t cos(θ) - e^{M |t|} sin(0.3 t) sin(θ)

y(t) = 42 + t sin(θ) + e^{M |t|} sin(0.3 t) cos(θ)

#### 3. Loss Function Construction

Used mean L1 distance for fitting:

L1 loss = (1/N) Σ_{i=1}^N ( | x_i^{true} - x_i^{model} | + | y_i^{true} - y_i^{model} | )

This loss matches the assignment's scoring criterion.

#### 4. Optimization

Applied scipy.optimize.minimize with method "L-BFGS-B".

Set parameter bounds and initial guesses.

Minimized the L1 loss to extract optimal values for θ, M, X.

#### 5. Result Extraction and Validation

Recorded extracted parameter values and the final mean L1 loss.

Substituted results into the parametric equation for submission.
