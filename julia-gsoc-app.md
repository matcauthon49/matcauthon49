# JuliaStats: New Statistical Frameworks for Time Series and Event Studies Analysis

## Abstract
Julia's present infrastructure for handling time series-related data is incomplete, inefficient and unsuited to perform rigorous statistical analysis on large datasets. The goal of this project is to develop and publish two public Julia packages that provide a robust implementation of time series that is appealing to researchers working with time series data (with a particular focus on financial statistics) and are competitive with the leading industry tools - R's `xts` package, and the time series functionality of python's `pandas`.

Project Category: [JuliaStats Improvements](https://julialang.org/jsoc/gsoc/juliastats)

Mentors: [Chirag Anand](https://github.com/chiraganand), [Ayush Patnaik](https://github.com/ayushpatnaikgit)

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

2. EventStudies.jl: A package designed for performing event studies of time series data using daily returns used in financial economics. `EventStudies.jl` will use the TSx package as its basis for TimeSeries data storage and its goal will be to implement the functionality outlined in [this paper](https://rdrr.io/cran/eventstudies/f/inst/doc/eventstudies.pdf), which serves as an introduction to the eventstudies package in `R`:
    1. `eventstudy()`

### Who is this for?

Both these packages are for statistical (especially financial) researchers who need a familiar environment for general time series work in Julia. The packages will be designed for easy migration from `R` (currently the statistician's developmental tool of choice). The TSx package has been designed with current industry professionals and will allow the best system of financial datasets in Julia so far.

EventStudies is a technical package which will allow financial researchers to perform event studies on daily returns data of firms. The event study method is a standard method that is utilized in predicting impacts of notable events on stock price changes, and has been utilized on all kinds of data from accounting and marketing to supply chain management. Event Studies work by 

## Code Portfolio

I have worked on the alpha version of `TSx.jl` in collaboration with my proposed mentors, Chirag Anand and Ayush Patnaik. The code for this can be found [here](https://github.com/xKDR/TSx.jl). In particular I am familiar with the development process in Julia and am experienced in testing and documentation. 

My contributions have included:

1. Writing the code for several base functions, including `lag`, `pctchange`, and `diff`: [7d8e9ae](7d8e9aec8d59698cd69de45c733387de540d088d)
2. More efficient implementations of basic features like constructors and indexing: [e45b659](e45b65911d84e7983e16fd29d21e0136fc62070f)
3. Writing documentation: [0c88b26](0c88b26ab252116a30fa323ddcc544bed6727f13)

and a variety of bug fixes, issues, etc.

## Deliverables

At the end of the project I expect to publish a stable v1.0 release of `TSx.jl` and at least a v0.1 release of `EventStudies.jl` that contain the features listed under Goals. This should be achievable since `TSx.jl` currently has working code and simple implementations of the basic functionality I expect to provide. Early documentation, testing, and benchmarking has delivered promising returns. 

## About Me

### Specifics

1. Name: Naman Kumar
2. Occupation: Student, Chennai Mathematical Institute, India
3. Education: Undergrad, Mathematics and Computer Science
4. Email: namankr02@gmail.com
5. Github: [matcauthon49](https://github.com/matcauthon49)

### General Information

Hi! I'm currently an undergrad student dual majoring in Mathematics and Computer Science. I love programming as a tool to see beautiful applications of the theoretical scientific and mathematical ideas and firmly believe in the power of computers to obtain groundbreaking results in scientific fields. I began programming competitively to implement wonderful algorithms and be breathtaken by the crazy applications they had to all kinds of mathematical problems. I used C++ and Python for solving hard competition problems and eventually became interested in systems and open-source programming to actually help implement these very algorithms into base code that would be used for a plethora of purposes.

I initially began to program in Julia once it became clear that its 'best-of-both-worlds' approach to programming made it the language to go to for scientific applications. During the past months I have academically simulated various graph games and run analyses of their results for courses in Julia and have contributed to the development of the `TSx.jl` package which I have linked above. 

As an advanced mathematics undergrad I believe I possess most of the technical statistics-based background that is required to complete this project and have taken advanced algorithms courses in college. I am also ready and eager to learn more statistics skills required for the task.
