A repository of (tabulated) degenerate neutron capture rates.
## Reaction Rates

The repo is sorted into folders by proton number, followed by files for each isotope. The folder structure is given by
z{ZZZ}/z{ZZZ}n{NNN}.dat where Z and N are integers for the respective number of protons/neutrons.

Each file is a long-format grid. The first column is the temperature (in GK), the second column is the chemical potential (in MeV), the third column is the degenerate reaction rate (in  [$cm^3 mol^{-1} s^{-1}$]), the fourth column is the classical reaction rate ( in [$cm^3 mol^{-1} s^{-1}$] and the fifth column is the ratio between the degenerate and classical rate. All reaction rates are calculated using the stellar cross section (ie, including excited states of the target nucleus).


There are 33 temperature values that are set as:

```
T = [1.0e-04, 5.0e-04, 1.0e-03, 5.0e-03, 1.0e-02, 5.0e-02, 1.0e-01, 2.0e-01, 2.5e-01,
 3.0e-01, 4.0e-01, 5.0e-01, 6.0e-01, 7.0e-01, 8.0e-01, 9.0e-01, 1.0e+00, 1.5e+00,
 2.0e+00, 2.5e+00, 3.0e+00, 3.5e+00, 4.0e+00, 5.0e+00, 6.0e+00, 7.0e+00, 8.0e+00,
 9.0e+00, 1.0e+01, 2.0e+01, 3.0e+01, 4.0e+01, 5.0e+01] .
```
There are also 80 Chemical potential values. The first 40 points range from 0 to 0.2 MeV with a spacing of 0.005 MeV, followed by the remaining 40 points with a spacing of 0.2 MeV until a maximum of 8 MeV. The array can be constructed (in python) via

```mu = np.append(np.arange(0, 0.2, 0.005), np.arange(0.2, 8.2, 0.2))```

or hardcoded

```
mu = [0.00e+00, 5.00e-03, 1.00e-02, 1.50e-02, 2.00e-02, 2.50e-02,
       3.00e-02, 3.50e-02, 4.00e-02, 4.50e-02, 5.00e-02, 5.50e-02,
       6.00e-02, 6.50e-02, 7.00e-02, 7.50e-02, 8.00e-02, 8.50e-02,
       9.00e-02, 9.50e-02, 1.00e-01, 1.05e-01, 1.10e-01, 1.15e-01,
       1.20e-01, 1.25e-01, 1.30e-01, 1.35e-01, 1.40e-01, 1.45e-01,
       1.50e-01, 1.55e-01, 1.60e-01, 1.65e-01, 1.70e-01, 1.75e-01,
       1.80e-01, 1.85e-01, 1.90e-01, 1.95e-01, 2.00e-01, 4.00e-01,
       6.00e-01, 8.00e-01, 1.00e+00, 1.20e+00, 1.40e+00, 1.60e+00,
       1.80e+00, 2.00e+00, 2.20e+00, 2.40e+00, 2.60e+00, 2.80e+00,
       3.00e+00, 3.20e+00, 3.40e+00, 3.60e+00, 3.80e+00, 4.00e+00,
       4.20e+00, 4.40e+00, 4.60e+00, 4.80e+00, 5.00e+00, 5.20e+00,
       5.40e+00, 5.60e+00, 5.80e+00, 6.00e+00, 6.20e+00, 6.40e+00,
       6.60e+00, 6.80e+00, 7.00e+00, 7.20e+00, 7.40e+00, 7.60e+00,
       7.80e+00, 8.00e+00]
```

Each reaction rate file entry is formatted as '%.6e', with a tab spacing between each column.

## Partition functions
We also provide partition functions used for in the calculation of the stellar cross section $G_0(T)$ - all of which have been normalized to the ground state:
$G_0(T) = G(T)/g_0$ where $g_0 = 2J + 1$ is the spin degeneracy of the targets ground state.
For convience, we also provide the *non normalized* partition functions G(T). The ground-state normalized files are found in the folder G_0, while non-normalized are found in the folder G.
The file structure is very similar to the rates, where each isotope follows the same n, z naming convention. Each file contains 2 columns, the first column is temperature and the second being the (non/normalized) partition function.
Note that our calculations only use discrete states of the target nucleus, so we do not extend our partition function into a continuum. 

## Q values
The file Q_vals.dat in the root directory contain all corresponding Q values corresponding to the cross section calculations. All of our masses use experimental information if present, or use the HFB model from TALYS for theoretical masses. The first column of this file is the atomic number z, the second column is the neutron number n, and the last column is the Q value of reaction in MeV. The formatting string for each row is ``` %i    %i    6.4f ```