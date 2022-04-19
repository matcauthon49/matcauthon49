# JuliaStats: New Statistical Frameworks for Time Series and Event Studies Analysis

## Abstract
Julia's present infrastructure for handling time series-related data is incomplete, inefficient and unsuited to perform rigorous statistical analysis on large datasets. The goal of this project is to develop and publish two public Julia packages that provide a robust implementation of time series that is appealing to researchers working with time series data (with a particular focus on financial statistics) and are competitive with the leading industry tools - R's `xts` package, and the time series functionality of python's `pandas`.

## The Project

### Goals

The goal of the project is the development of the following two Julia Packages:

1. TSx.jl: A general time series package that defines a time series class which retains the structure and efficient methods of `DataFrames.jl` and provides the necessary time series management functionality, including but not limited to:
    1. Indexing: Methods for efficient `Date` and `DateTime` based indexing that includes timestamp and period-based indexing.
    2. Resampling: Methods for efficient conversion of time series data to the required period index based on default user-defined functions.
    3. Function Application: Methods for efficient application, aggregation and frequency conversion.
    4. Time Span/Zone Representation: Infrastructure for extending time series analysis in Julia to non-base DateTime types such as Business Days, non-standard week types and other common stock period types, along with clean time zone transformations.
    5. Integration with other Julia libraries: Quick support for Plots.jl, Statistics.jl and Distributions.jl that allows easy visualization and operations.
 
TSx defines the core timeseries object, the `TS` object, as a DataFrame wrapper that contains a special `Index` field that provides the necessary time integration. Because TSx will use standard DataFrames as its core data, it will provide a clean interface and access to native DataFrames functions.

2. EventStudies.jl

### Who is this for?

Both these packages are for statistical (especially financial) researchers who need a familiar environment for general time series work in Julia. The packages will be designed for easy migration from `R` (currently the statistician's developmental tool of choice). 

## Code Portfolio

I have worked on the alpha version of `TSx.jl` in collaboration with my proposed mentors, Chirag Anand and Ayush Patnaik. The code for this can be found [here](https://github.com/xKDR/TSx.jl). In particular I am familiar with the development process in Julia and am experienced in testing and documentation. 

## Deliverables

At the end of the project I expect to publish a stable v1.0 release of `TSx.jl` and at least a v0.1 release of `EventStudies.jl` that contain the features listed under Goals. This should be achievable since `TSx.jl` currently has working code and simple implementations of the basic functionality I expect to provide. Early documentation, testing, and benchmarking has delivered promising returns. 
