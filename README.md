A repository of (tabulated) degenerate neutron capture rates.

The repo is sorted into folders by proton number, followed by files for each isotope. The folder structure is given by
z{ZZZ}/z{ZZZ}n{NNN}.dat where Z and N are integers for the respective number of protons/neutrons.

Each file is a wide-format grid. Each coloumn represents a different temperature, and each row is for a different chemical potnential.
There are 33 temperature values (coloumns) in units of GK that are set as:

T = [1.0e-04, 5.0e-04, 1.0e-03, 5.0e-03, 1.0e-02, 5.0e-02, 1.0e-01, 2.0e-01, 2.5e-01,
 3.0e-01, 4.0e-01, 5.0e-01, 6.0e-01, 7.0e-01, 8.0e-01, 9.0e-01, 1.0e+00, 1.5e+00,
 2.0e+00, 2.5e+00, 3.0e+00, 3.5e+00, 4.0e+00, 5.0e+00, 6.0e+00, 7.0e+00, 8.0e+00,
 9.0e+00, 1.0e+01, 2.0e+01, 3.0e+01, 4.0e+01, 5.0e+01] .

There are also 90 Chemical potential values (rows) in units of MeV. The first 10 points range from 0 to 0.25 MeV with a spacing of 0.025 MeV, followed by the remaining 80 points with a spacing of 0.25 MeV until a maximum of 20 MeV. The array can be constructed (in python) via

np.append(np.arange(0, 0.25, 0.025), np.arange(0.25, 20.25, 0.25))

or hardcoded

Chem = [ 0.   ,  0.025,  0.05 ,  0.075,  0.1  ,  0.125,  0.15 ,  0.175,
        0.2  ,  0.225,  0.25 ,  0.5  ,  0.75 ,  1.   ,  1.25 ,  1.5  ,
        1.75 ,  2.   ,  2.25 ,  2.5  ,  2.75 ,  3.   ,  3.25 ,  3.5  ,
        3.75 ,  4.   ,  4.25 ,  4.5  ,  4.75 ,  5.   ,  5.25 ,  5.5  ,
        5.75 ,  6.   ,  6.25 ,  6.5  ,  6.75 ,  7.   ,  7.25 ,  7.5  ,
        7.75 ,  8.   ,  8.25 ,  8.5  ,  8.75 ,  9.   ,  9.25 ,  9.5  ,
        9.75 , 10.   , 10.25 , 10.5  , 10.75 , 11.   , 11.25 , 11.5  ,
       11.75 , 12.   , 12.25 , 12.5  , 12.75 , 13.   , 13.25 , 13.5  ,
       13.75 , 14.   , 14.25 , 14.5  , 14.75 , 15.   , 15.25 , 15.5  ,
       15.75 , 16.   , 16.25 , 16.5  , 16.75 , 17.   , 17.25 , 17.5  ,
       17.75 , 18.   , 18.25 , 18.5  , 18.75 , 19.   , 19.25 , 19.5  ,
       19.75 , 20.   ] .

Each data entry is in %.6e formatting, with single spaces between coloumns. The units of the reaction rates are [$cm^3 mol^{-1} s^{-1}$]