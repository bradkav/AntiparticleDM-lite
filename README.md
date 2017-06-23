# AntiparticleDM

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.815457.svg)](https://doi.org/10.5281/zenodo.815457)

Python code for calculating the prospects of future direct detection experiments to discrimination between Majorana and Dirac Dark Matter (i.e. to determine whether Dark Matter is its own antiparticle).

Direct detection event rates and mock data generation are taken care of by a variation of the `WIMpy` code - available [here](https://github.com/bradkav/WIMpy/tree/Antiparticle).

With this code, the results of arXiv:XXXX.XXXXX should be **entirely reproducible**. Follow the instructions under [below](#repro) if you want to reproduce those results. If you find any mistakes or have any trouble reproducing the results, please get in touch.

If you have any questions, comments, bug-reports etc., please contact Bradley Kavanagh at bradkav@gmail.com. 

### Version History

## Contents

- `calc`: core code for calculating the statistical significance for discriminating between Dirac and Majorana Dark Matter (DM).
- `analysis`: scripts for processing the results and generating plots.
- `results`: data products for a range of DM masses, couplings and experimental ensembles.
- `plots`: plots from arXiv:XXXX.XXXXX (and others).

## Reproducing the results <a name="repro"></a>

The majority of the code is written in `python`, and requires the standard `numpy` and `scipy` libraries. For plotting, `matplotlib` is also required.

### Performing likelihood fits

Code for generating mock data sets and performing likelihood fits are found in the `calc` folder. 

The module `CalcDiscrimination.py` does the heavy lifting. If you want to calculate the discrimination significance for a particular ensemble and parameter point, use:

```python
import CalcDiscrimination as CD
CD.CalcDiscrim(ensemble, m0, f, r_np)
```

where `m0` is the DM mass in GeV, `f` is the interference factor (Eq. 6) and `r_np` is the ratio of neutron to proton couplings (Eq. 5 over Eq. 4).

`python CalcDiscrimination.py ENSEMBLE MASS INDEX DIR`

If you're interested in calculating the discrimination significance for a particular parameter point and ensemble, you can use 

The python script `CalcDiscrimination.py` is used to calculate the significance achievable with a particular set of experiments and a particular set of input Dark Matter parameters. It is called as:



Here, `ENSEMBLE` specifies which experimental ensemble to use `A`, `B`, `C` or `D`. `MASS` specifies the input DM mass in GeV. `INDEX` specifies the input DM couplings (in particular, in indexes the points on a grid of couplings).

`WIMpy` generates 50 mock data sets based on the input parameter points. For each data set, it uses a grid-refinement method to calculate the maximum likelihood and therefore the significance for discrimination between Dirac-like and Majorana-like couplings. The significances are output to a file named `Results_pINDEX.txt` in the relative path `DIR`.

### Checking the likelihood calculator

`CompareNgrid.py`

### Plotting



## Citation

If you make use of the code or the numerical results, please cite the project as:

`Kavanagh, B. J., Queiroz, F. S., Rodejohann, W., Yaguna, C. E., AntiparticleDM (2017), https://github.com/bradkav/AntiparticleDM/`

Please also cite...

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
