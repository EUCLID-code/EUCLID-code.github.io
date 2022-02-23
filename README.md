# Introduction
EUCLID (Efficient Unsupervised Constitutive Law Identification & Discovery) utilizes displacement and reaction force data, but no stress data as these are not available from experiments, to discover material laws as compact and interpretable mathematical formulas. A large catalog of candidate material models is constructed out of which dominant candidates are selected through sparse regression. To compensate the unavailability of stress data, physics knowledge is employed by minimizing the sum of squared residuals of the weak linear momentum balance.

![Schematic of EUCLID](./img/schematics.png)

Full-field displacement and net reaction force data that are obtained from a single experiment (a) serve as input data for EUCLID. The displacement data (b) is interpolated (c) to obtain the displacement field (d) and after differentiation the strain field (e). A general material model library is constructed, which can describe a variety of different material responses dependent on the choice of material parameters `theta`. Based on the model library, the stresses (f) and hence the residuals of the weak linear momentum balance (g,h) can be expressed dependent on the unknown parameters `theta`. The linear momentum balance serves as a physical constraint on the material parameter space. Minimizing the  sum of squared residuals together with a sparsity promoting regularization term (i) yields a sparse parameter vector `theta` and hence an interpretable constitutive law expressed by a compact mathematical formula (j).

# Applications

## Hyperelasticity
EUCLID was successfully demonstrated to be able to discover strain energy density functions of hyperelastic materials (see Ref. 1.).
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-hyperelasticity" target="_blank">GitHub</a>
and the <a href="https://www.research-collection.ethz.ch/handle/20.500.11850/505693" target="_blank">ETH Research Collection</a>, respectively.
The corresponding documentation can be found <a href="https://EUCLID-code.github.io/EUCLID-hyperelasticity/mkdocs/site" target="_blank">here</a>.

## Elasto-Plasticity
In Ref. 2., EUCLID was for the first time applied to discover path-dependent material behavior, i.e., elasto-plastic material models.

coming soon ..

# References

1.	Moritz Flaschel<span>&#42;</span>, Siddhant Kumar<span>&#42;</span> and Laura De Lorenzis (<span>&#42;</span>contributed equally)  
	__Unsupervised discovery of interpretable hyperelastic constitutive laws__  
	_Computer Methods in Applied Mechanics and Engineering, 381, p.113852_ ([open access](https://www.sciencedirect.com/science/article/pii/S0045782521001894))

2.	Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis
	__Discovering plasticity models without stress data__
	([open access](https://arxiv.org/pdf/2202.04916.pdf))
