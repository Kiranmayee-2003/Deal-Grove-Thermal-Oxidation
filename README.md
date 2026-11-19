# Deal-Grove Thermal Oxidation Model for Silicon



A Python model of dry and wet thermal oxidation of silicon using the Deal-Grove relation, x² + A·x = B·(t + τ). It computes oxide thickness against time and temperature, the time needed to reach a target thickness, and multi-step sequences such as dry-wet-dry.

**Tools:** Python (NumPy, SciPy, Matplotlib). Runs in Google Colab with no installs.
**Author:** Kiranmayee Vaddepally, M.Tech, Quantum and Solid State Devices, IIT Hyderabad



## How to run

1. Open `Deal_Grove_Thermal_Oxidation.ipynb` in [Google Colab](https://colab.research.google.com) (File > Upload notebook).
2. Choose Runtime > Run all.
3. Change the values in the **Inputs** cell (temperatures, silicon orientation, target thickness) and re-run.



## What the model does

1. Computes the rate constants B and B/A from Arrhenius laws for dry and wet oxidation (Si(111), with Si(100) obtained by dividing B/A by 1.68).
2. Solves the Deal-Grove relation in closed form for oxide thickness against time.
3. Finds the time needed to grow a target oxide thickness.
4. Carries the oxide thickness from one step to the next, so multi-step sequences can be modelled.



## Checks

* The closed-form solution matches direct numerical integration of dx/dt = B/(A + 2x) to four decimal places in nanometres.
* The Arrhenius rate constants agree with a second published table within about 20% in the worst case and typically within 10%, so thicknesses are good to roughly that level.



## Example results (Si(100))

* 100 nm of oxide at 1000 °C: about 191 min dry, about 10 min wet.
* 100 nm of oxide at 1100 °C: about 61 min dry, about 3 min wet.
* Illustrative dry-wet-dry sequence at 1100 °C (10, 20, 10 min): about 349 nm. This is an example, not a real fab recipe.



## Sources

* CityU AP6120, chapter 4 (oxidation), Tables 4.1 and 4.2: https://www.cityu.edu.hk/phy/appkchu/AP6120/4.PDF
* TU Wien, Hollauer thesis, Deal-Grove model and Table 2.2: https://www.iue.tuwien.ac.at/phd/hollauer/node16.html
* Original model: B. E. Deal and A. S. Grove, J. Appl. Phys. 36, 3770 (1965)



## Assumptions and limitations

* The model underestimates dry oxide growth below about 25 nm, where an extra fast initial regime exists.
* Constant temperature in each step, instant ramp, pure O₂ or H₂O at 1 atm. No pressure or doping dependence.
* Silicon consumption is not tracked.
* This is a first-principles model of the basic physics, not a replacement for a process simulator.

