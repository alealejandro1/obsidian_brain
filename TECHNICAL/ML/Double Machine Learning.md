keywords:: Double Machine Learning, Treatment, Control, Causality, OLS

# Orthogonal/Double Machine Learning[](https://econml.azurewebsites.net/spec/estimation/dml.html#orthogonal-double-machine-learning "Permalink to this headline")

## What is it?[](https://econml.azurewebsites.net/spec/estimation/dml.html#what-is-it "Permalink to this headline")

Double Machine Learning is a method for estimating (heterogeneous) treatment effects when all potential confounders/controls (factors that simultaneously had a direct effect on the treatment decision in the collected data and the observed outcome) are observed, but are either too many (high-dimensional) for classical statistical approaches to be applicable or their effect on the treatment and outcome cannot be satisfactorily modeled by parametric functions (non-parametric). Both of these latter problems can be addressed via machine learning techniques (see e.g. [[Chernozhukov2016]](https://econml.azurewebsites.net/spec/references.html#chernozhukov2016)).

The method reduces the problem to first estimating _two predictive tasks_:

> 1.  predicting the outcome from the controls,
>     
> 2.  predicting the treatment from the controls;


Overcoming selection bias?
Having independent residuals?
OLS assumes dependency of covariates is linear?