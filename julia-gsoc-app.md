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
 
TSx defines the core timeseries object, the `TS` object, as a DataFrame wrapper that contains a special `Index` field that provides the necessary time integration. Because TSx will use standard DataFrames as its core data, it will provide a clean interface and access to native DataFrames functions. The pre-existing time series package, `TimeSeries.jl`, does not offer the flexibility of this approach and instead defines its own `Tables.jl` type interface which does not allow, among other things, code inheritance, addition of new features, easy transformation of data, and appropriate resampling and aggregation features. In my opinion the better approach for making Julia a competitor to R in terms of time series handling is the one that TSx carries.

2. EventStudies.jl: A package designed for performing event studies of time series data using daily returns used in financial economics. `EventStudies.jl` will use the TSx package as its basis for TimeSeries data storage and its goal will be to implement the functionality outlined in [this paper](https://rdrr.io/cran/eventstudies/f/inst/doc/eventstudies.pdf), which serves as an introduction to the eventstudies package in `R`:
    1. Model Creation: Implementation of a market model that invokes a time-series regression which captures market-wide fluctuations. This will also be expanded to include augmented market models.
    2. The `eventstudy` object: The actual process of the eventstudy will work via creation of the `eventstudy` object, which takes in the underlying dataset, types of inference strategy, historical datasets and windowing parameters and returns a complete and rigorous event study of the process.

As seen, the ideas behind event study are in a beta stage. The concept of how event study will be implemented in Julia will be refined further.

### Who is this for?

Both these packages are for statistical (especially financial) researchers who need a familiar environment for general time series work in Julia. The packages will be designed for easy migration from `R` (currently the statistician's developmental tool of choice). The TSx package has been designed with current industry professionals and will allow the best system of financial datasets in Julia so far. 

EventStudies is a technical package which will allow financial researchers to perform event studies on daily returns data of firms. The event study method is a standard method that is utilized in predicting impacts of notable events on stock price changes, and has been utilized on all kinds of data from accounting and marketing to supply chain management. Event Studies work by creating appropriate models of data and then computing differences between simulated and actual returns during the event period. The goal of `EventStudies.jl` is to provide the most efficient infrastructure required to accomplish this.

### Priorities

In order of priority, API, Docs, Features, Testing and Developer Docs.

In my experience the development of a good API is crucial for the usability, longevity, and overall integrity of any package. Writing a usable API is a fairly non trivial art form. My first priority will be to write clean, efficient signatures and easy lookups supported with excellent documentation. Documentation is a must since both packages carry the implicit assumption that a large subset of users will be

1. People who are researchers who require the use of the package for applications, and
2. Migratory users who might be new to analysis in Julia.

The goal of TSx is to create a lightweight but highly usable framework for time series work in Julia. As such, the package will be designed with its DataFrames core in mind: instead of providing increasing amount of functions to perform actions (a problem that `TimeSeries.jl` currently falls into) the focus will be on allowing as much leeway for custom applications as possible, since time series work by nature is such that the operations to be performed are unpredictable. For `EventStudies.jl` the ultimate goal will be for the user to get to choose what kind of modelling they would like to use.

I will also be spending a significant amount of time writing excellent tests to ensure that the package performs correctly under all circumstances and throws the correct errors when appropriate. This is important, again, because time series work is unpredictable in nature.

Finally a good developer doc is always required to ensure code maintainance to potential developers.

### Milestones and Timeline

#### May 20 - June 12 (Community Bonding Period)

I can begin coding from this point already since I am already working on the package. This period will involve trivial bug fixes and general efficiency improvement such as removal of `insertcols()` instances, using better indexing procedures, efficiency improvements to written code, etc. The `EventStudies.jl` concept will take full shape in this period, and the specifics of package structure and understanding the ways TSx will be used in its development will be completed. Some test cases for future work will also be written in this period.

#### Week 1

Restructuring of `Dates` as an index type in `TSx.jl`. Allowing access to user-defined date types as well as other date libraries such as `BusinessDays.jl`. This is required for accurate stock modelling and correct resampling.

#### Week 2

Addition of timezone functionality, and determination and implementation of missing data handling functions. Typing here is delicate and crucial for making sure that operations on time series work.

#### Weeks 3-4 

Implementation of robust aggregation and frequency conversion methods, along with checking code usability on testcases. Resampling based on timespan representations will also be implemented securely.

#### Weeks 5-6

Integration with (in order of priority) Plots.jl, CSV.jl, and Distributions.jl. This will be done without simply applying the functions to the underlying DataFrame (as has been done presently). The APIs will be carefully considered in order to provide maximum usability and flexibility to the underlying TS class.

#### Phase 1 Evaluation

First publication of the beta version of `TSx.jl` to be given to testers.

#### Week 7

Finalization of the structure of the `Eventstudies.jl` package, along with writing standard testing datasets for both packages. Remaining bug fixes for `TSx`.

#### Weeks 8-10

Bug fixes, testing, documentation for `TSx.jl`. Writing base code and model creation for `EventStudies.jl` which uses the TS object in `TSx.jl`.

#### Weeks 11-12

Bug fixes, testing, documentation and package registration for `TSx.jl`. Development of the `eventstudies()` method that provides the bulk of the functionality of `EventStudies.jl`. Once this has been done, `EventStudies.jl` should be usable.

#### Final Evaluation

v1.0 release of `TSx.jl`, followed by the first public beta of `EventStudies.jl`. 

### Stretch Goals

Yes! Being a statistical package, the addition of other statistical features to `TSx`, a complete developer documentation, introduction of multithreading and more analysis methods to `TSx.jl` can always be implemented. Similarly, extending `EventStudies` to a robust intraday event analysis and increasing the model methods to give users more flexibility over the internal algorithm will be done.

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

## Logistics

I have a research internship taking place from July 4 - July 31. Apart from 2-3 days of travel time throughout the whole period, this should not hamper my contribution in any significant way. My university resumes classes from August 31 onwards. From this point on I plan to reduce my time from 24-30 hours/week to around 12-16 hours/week. I have thus adjusted the timeline respectively.
