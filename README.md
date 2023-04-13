# Introduction
EUCLID (Efficient Unsupervised Constitutive Law Identification & Discovery) utilizes local displacement and global reaction force data,
but no local stress data as these are not available from experiments, to discover material models without assuming a specific functional form for the model a priori.
To this end, a large catalog of candidate material models is constructed out of which dominant candidates are selected through sparse regression
or the material behavior is described by a general machine learning based ansatz, e.g., a neural network.
To compensate the unavailability of stress data, physics knowledge is employed by minimizing the sum of squared residuals of the weak linear momentum balance.

![Schematic of EUCLID](./img/schematics.png)

<sub>Figure 1: EUCLID workflow.</sub>

The figure above shows the workflow of the sparse regression based EUCLID algorithm.
Full-field displacement and net reaction force data that are obtained from a single experiment (a) serve as input data for EUCLID.
The displacement data (b) is interpolated (c) to obtain the displacement field (d) and after differentiation the strain field (e).
A general material model library is constructed, which can describe a variety of different material responses dependent on the choice of material parameters `theta`.
Based on the model library, the stresses (f) and hence the residuals of the weak linear momentum balance (g,h) can be expressed dependent on the unknown parameters `theta`.
The linear momentum balance serves as a physical constraint on the material parameter space.
Minimizing the sum of squared residuals together with a sparsity promoting regularization term (i) yields a sparse parameter vector `theta`
and hence an interpretable constitutive law expressed by a compact mathematical formula (j).

# Applications

## Hyperelasticity
EUCLID was successfully demonstrated to be able to discover strain energy density functions of hyperelastic materials (see Ref. 1.).
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-hyperelasticity" target="_blank">GitHub</a> (see Ref. 2.)
and the <a href="https://www.research-collection.ethz.ch/handle/20.500.11850/505693" target="_blank">ETH Research Collection</a> (see Ref. 3.), respectively.
The documentation of the hyperelasticity code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-hyperelasticity/mkdocs/site" target="_blank">here</a>.

### Bayesian Inference
In Ref. 7., the problem of material model discovery was considered from a Bayesian perspective.
Through Markov Chain Monte Carlo sampling, the Bayesian-EUCLID deduces a posterior probability distribution for the unknown material parameters,
which is a joined distribution of the model likelihood and a sparsity promoting spike-and-slab prior.
In this way, parsimonious and interpretable material models can be discovered with quantifiable uncertainties. 
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-hyperelasticity-bayesian" target="_blank">GitHub</a>.
The documentation of the Bayesian-EUCLID code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-hyperelasticity-bayesian/mkdocs/site" target="_blank">here</a>.

### Neural networks

In Ref. 8, we demonstrate the use of neural networks for learning the hidden material models from full-field displacement and global reaction force data.
By using an Input Convex Neural Network (ICNN) and a physics guided training protocol, we ensure that the learned strain-stress relation fulfills multiple physical constraints. 
Moreover, we present the capability of our ICNN-based material model to learn the hidden fiber angle arrangments of anisotropic hyperelastic materials.
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-hyperelasticity-NN" target="_blank">GitHub</a> (see Ref. 8.).
The documentation of the NN-EUCLID code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-hyperelasticity-NN/mkdocs/site" target="_blank">here</a>.

<img src="/img/neural_network.png" alt="Neural network" width="600"/>

<sub>Figure 2: Neural network.</sub>

## Viscoelasticity
In Ref. 11, EUCLID is used to identify the material model of a viscoelastic material from full-field displacement and reaction force data in the frequency domain.
Starting from a large library of viscoelastic Maxwell elements, EUCLID automatically selects the most relevant elements using sparse regression and k-means clustering.

## Elasto-Plasticity
In Ref. 4., EUCLID was for the first time applied to discover elasto-plastic material models.
Full-field displacement and global reaction force data are used to discover plastic yield surfaces and hardening laws as closed-form mathematical formulas (see Animation 1).
The codes and data are publically available on <a href="https://github.com/EUCLID-code/EUCLID-plasticity" target="_blank">GitHub</a> (see Ref. 5.)
and the <a href="https://www.research-collection.ethz.ch/handle/20.500.11850/534002" target="_blank">ETH Research Collection</a> (see Ref. 6.), respectively.
The documentation of the elasto-plasticity code and an example can be found <a href="https://EUCLID-code.github.io/EUCLID-plasticity/mkdocs/site" target="_blank">here</a>.

<img src="/img/yield_surface_evolution.gif" alt="Yield Surface Evolution" width="400"/>

<sub>Animation 1: Comparison between the true and discovered yield surface evolution along a given deformation path.</sub>

## Generalized Standard Materials
In Ref. 9., the EUCLID framework is extended to generalized standard materials.
In this way, no a priori choice of a material class (such as hyperelasticity or elasto-plasticity) has to be made
and EUCLID can automatically discover the true hidden material model from a large catalog of constitutive classes, including elasticity, viscoelasticity, elastoplasticity, viscoplasticity, isotropic and kinematic hardening. 
<a href="https://github.com/EUCLID-code/EUCLID-plasticity" target="_blank">Codes</a> (see Ref. 5.),
<a href="https://www.research-collection.ethz.ch/handle/20.500.11850/586072" target="_blank">data</a> (see Ref. 10.), and a
<a href="https://EUCLID-code.github.io/EUCLID-plasticity/mkdocs/site" target="_blank">documentation</a> are publically available.

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
	_Computer Methods in Applied Mechanics and Engineering, 398, p.115225_ ([open access](https://www.sciencedirect.com/science/article/pii/S0045782522003681))  
	GitHub: [https://github.com/EUCLID-code/EUCLID-hyperelasticity-bayesian](https://github.com/EUCLID-code/EUCLID-hyperelasticity-bayesian)  

8.  Prakash Thakolkaran, Akshay Joshi, Yiwen Zheng, Moritz Flaschel, Laura De Lorenzis, Siddhant Kumar  
	__NN-EUCLID: deep-learning hyperelasticity without stress data__  
	_Journal of the Mechanics and Physics of Solids, 169, p.105076_ ([open access](https://doi.org/10.1016/j.jmps.2022.105076))  
	GitHub: [https://github.com/EUCLID-code/EUCLID-hyperelasticity-NN](https://github.com/EUCLID-code/EUCLID-hyperelasticity-NN)  

9.  Moritz Flaschel, Siddhant Kumar, Laura De Lorenzis  
	__Automated discovery of generalized standard material models with EUCLID__  
	_Computer Methods in Applied Mechanics and Engineering, 405, p.115867_ ([open access](https://www.sciencedirect.com/science/article/pii/S0045782522008234))  

10.	Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis  
	__FEM Data - Automated discovery of generalized standard material models with EUCLID__  
	_ETH Research Collection_  
	DOI: [https://doi.org/10.3929/ethz-b-000586072](https://doi.org/10.3929/ethz-b-000586072)  

11. Enzo Marino, Moritz Flaschel, Siddhant Kumar and Laura De Lorenzis  
	__Automated identification of linear viscoelastic constitutive laws with EUCLID__  
	[_Mechanics of Materials, 181, p.104643_](https://www.sciencedirect.com/science/article/abs/pii/S0167663623000893) ([open access preprint](http://arxiv.org/abs/2212.10969))  
	
11. Moritz Flaschel  
	__Automated Discovery of Material Models in Continuum Solid Mechanics__  
	([open access](https://doi.org/10.3929/ethz-b-000602750))  