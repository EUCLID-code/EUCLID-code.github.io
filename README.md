# Introduction
EUCLID (Efficient Unsupervised Constitutive Law Identification & Discovery) utilizes displacement and reaction force data, but no stress data as these are not available from experiments, to discover material laws as compact and interpretable mathematical formulas. A large catalog of candidate material models is constructed out of which dominant candidates are selected through sparse regression. To compensate the unavailability of stress data, physics knowledge is employed by minimizing the sum of squared residuals of the weak linear momentum balance.

![Schematic of EUCLID](./img/schematics.png)

Full-field displacement and net reaction force data that are obtained from a single experiment (a) serve as input data for EUCLID. The displacement data (b) is interpolated (c) to obtain the displacement field (d) and after differentiation the strain field (e). A general material model library is constructed, which can describe a variety of different material responses dependent on the choice of material parameters `theta`. Based on the model library, the stresses (f) and hence the residuals of the weak linear momentum balance (g,h) can be expressed dependent on the unknown parameters `theta`. The linear momentum balance serves as a physical constraint on the material parameter space. Minimizing the  sum of squared residuals together with a sparsity promoting regularization term (i) yields a sparse parameter vector `theta` and hence an interpretable constitutive law expressed by a compact mathematical formula (j).

# Applications

## Hyperelasticity
EUCLID was successfully demonstrated to be able to discover strain energy density functions of hyperelastic materials (see Ref. 1.).
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-hyperelasticity" target="_blank">GitHub</a> (see Ref. 2.)
and the <a href="https://www.research-collection.ethz.ch/handle/20.500.11850/505693" target="_blank">ETH Research Collection</a> (see Ref. 3.), respectively.
The documentation of the hyperelasticity code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-hyperelasticity/mkdocs/site" target="_blank">here</a>.

## Elasto-Plasticity
In Ref. 4., EUCLID was for the first time applied to discover path-dependent material behavior, i.e., elasto-plastic material models.
In this application of EUCLID, the full-field displacement and global reaction force data are used to discover plastic yield surfaces and hardening laws as closed-form mathematical formulas (see Animation 1).
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-plasticity" target="_blank">GitHub</a> (see Ref. 5.)
and the <a href="https://www.research-collection.ethz.ch/handle/20.500.11850/534002" target="_blank">ETH Research Collection</a> (see Ref. 6.), respectively.
The documentation of the elasto-plasticity code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-plasticity/mkdocs/site" target="_blank">here</a>.

<img src="/img/yield_surface_evolution.gif" alt="Yield Surface Evolution" width="400"/>

<sub>Animation 1: Comparison between the true and discovered yield surface evolution along a given deformation path.</sub>

# References

1.	Moritz Flaschel<span>&#42;</span>, Siddhant Kumar<span>&#42;</span> and Laura De Lorenzis (<span>&#42;</span>contributed equally)  
	__Unsupervised discovery of interpretable hyperelastic constitutive laws__  
	_Computer Methods in Applied Mechanics and Engineering, 381, p.113852_ ([open access](https://www.sciencedirect.com/science/article/pii/S0045782521001894))

2.	Moritz Flaschel<span>&#42;</span>, Siddhant Kumar<span>&#42;</span> and Laura De Lorenzis (<span>&#42;</span>contributed equally)  
	__Supplementary software for "Unsupervised discovery of interpretable hyperelastic constitutive laws"__  
	_ETH Library_  
	DOI: [http://doi.org/10.5905/ethz-1007-508](http://doi.org/10.5905/ethz-1007-508)  
	GitHub: [https://github.com/EUCLID-code/EUCLID-hyperelasticity](https://github.com/EUCLID-code/EUCLID-hyperelasticity)

3.	Moritz Flaschel<span>&#42;</span>, Siddhant Kumar<span>&#42;</span> and Laura De Lorenzis (<span>&#42;</span>contributed equally)  
	__FEM Data – Unsupervised discovery of interpretable hyperelastic constitutive laws__  
	_ETH Research Collection_  
	DOI: [https://doi.org/10.3929/ethz-b-000505693](https://doi.org/10.3929/ethz-b-000505693)

4.	Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis  
	__Discovering plasticity models without stress data__  
	_npj Computational Materials, 8, 91 (2022)_ ([open access](https://rdcu.be/cMjUx))

5.	Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis  
	__Supplementary software for "Discovering plasticity models without stress data"__  
	_ETH Library_  
	DOI: [http://doi.org/10.5905/ethz-1007-509](http://doi.org/10.5905/ethz-1007-509)  
	GitHub: [https://github.com/EUCLID-code/EUCLID-plasticity](https://github.com/EUCLID-code/EUCLID-plasticity)

6.	Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis  
	__FEM Data - Discovering plasticity models without stress data__  
	_ETH Research Collection_  
	DOI: [https://doi.org/10.3929/ethz-b-000534002](https://doi.org/10.3929/ethz-b-000534002)

7.  Akshay Joshi, Prakash Thakolkaran, Yiwen Zheng, Maxime Escande, Moritz Flaschel, Laura De Lorenzis, Siddhant Kumar
	__Bayesian-EUCLID: discovering hyperelastic material laws with uncertainties__
	([open access](https://arxiv.org/abs/2203.07422))
