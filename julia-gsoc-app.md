# JuliaStats: New Statistical Frameworks for Time Series and Event Studies Analysis

## Abstract
Julia's present infrastructure for handling time series-related data is incomplete, inefficient and unsuited to perform rigorous statistical analysis on large datasets. The goal of this project is to develop and publish two public Julia packages that provide a robust implementation of time series that is appealing to researchers working with time series data (with a particular focus on financial statistics) and are competitive with the leading industry tools - R's `xts` package, and the time series functionality of python's `pandas`.

1. TSx.jl: A general time series package that defines a time series class which adapts the structure and efficient methods of `DataFrames.jl`
