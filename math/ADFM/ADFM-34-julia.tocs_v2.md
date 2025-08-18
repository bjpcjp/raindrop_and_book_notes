- Julia
  - G.1 Types
    - G.1.1 Booleans  
      The Boolean type Bool includes values true and false, which can be assigned to variables with any valid Unicode name. Standard Boolean operators such as not (!), and (&&), and or (||) are supported. Comments are denoted by the # symbol. For further details, see [Julia Bool Type](https://docs.julialang.org/en/v1/base/base/#Base.Bool).
    - G.1.2 Numbers  
      Julia supports integers (Int64) and floating-point numbers (Float64), with standard arithmetic and comparison operations. Division of integers produces a Float64. Type inference depends on machine architecture, e.g., Int32 on 32-bit systems. See [Julia Numbers](https://docs.julialang.org/en/v1/manual/types/#Numbers).
    - G.1.3 Strings  
      Strings are arrays of characters enclosed in double quotes and primarily used for error reporting in this text. The type is String. For more, see [Julia Strings](https://docs.julialang.org/en/v1/manual/strings/).
    - G.1.4 Vectors  
      Vectors are one-dimensional arrays created via square brackets with comma-separated elements, supporting various constructors such as trues, ones, zeros, and rand. Indexing begins at 1, supports ranges and reverse indexing, and many operations including push!, pop!, concatenation, sorting, and elementwise broadcasting. Refer to [Julia Arrays](https://docs.julialang.org/en/v1/manual/arrays/).
    - G.1.5 Matrices  
      Matrices are two-dimensional arrays created using spaces to separate elements and semicolons to separate rows. They support indexing, submatrix extraction, special matrix constructors (identity, diagonal, zeros, rand), and matrix operations including transposition, inversion, determinant, concatenation, and elementwise functions. Visit [Julia Matrices](https://docs.julialang.org/en/v1/manual/arrays/#Manual-Multidimensional-Arrays).
    - G.1.6 Tuples  
      Tuples are immutable ordered lists supporting mixed types, constructed with parentheses. They allow indexing and slicing but not mutation. Length can be accessed with length(). See [Julia Tuples](https://docs.julialang.org/en/v1/manual/types/#Tuples).
    - G.1.7 Named Tuples  
      Named tuples extend tuples by associating each element with a field name, supporting access by names as well as tuple unpacking. Their type includes field names and types. For reference, see [Julia Named Tuples](https://docs.julialang.org/en/v1/manual/types/#Named-Tuples).
    - G.1.8 Dictionaries  
      Dictionaries store key-value pairs, created either empty or with initial pairs using the => operator. Keys and values are accessed via square brackets, and haskey() checks key presence. The type signature encodes key and value types. More details at [Julia Dictionaries](https://docs.julialang.org/en/v1/manual/collections/#Dictionaries).
    - G.1.9 Composite Types  
      Composite types group named fields into potentially immutable or mutable structures using struct or mutable struct. Fields can optionally have type annotations enabling performance optimizations. Instances are created by calling the type with field values. Learn more at [Julia Composite Types](https://docs.julialang.org/en/v1/manual/types/#Composite-Types).
    - G.1.10 Abstract Types  
      Abstract types form a hierarchy over concrete types, acting as supertypes that cannot be instantiated themselves. The Float64 type hierarchy traces up from Float64 to AbstractFloat, Real, Number, and Any. Abstract types can be user-defined to organize subtypes. See [Julia Type Hierarchy](https://docs.julialang.org/en/v1/manual/types/#Type-Hierarchy).
    - G.1.11 Parametric Types  
      Parametric types accept parameters enclosed in braces to allow flexible typing, e.g., Dict{Int64,Int64} specifies key and value types. Users can define their own parametric types, though this text does not cover such definitions. For more, see [Julia Parametric Types](https://docs.julialang.org/en/v1/manual/types/#Parametric-Types).
  - G.2 Functions
    - G.2.1 Named Functions  
      Named functions are defined using the function keyword or concise assignment form with arguments enclosed in parentheses. Functions map argument tuples to return values and can be called with parameters. Further info at [Julia Functions](https://docs.julialang.org/en/v1/manual/functions/).
    - G.2.2 Anonymous Functions  
      Anonymous functions lack a name and can be assigned to variables. They use the arrow syntax (x -> expression) and can be passed as arguments to other functions for inline computation. See [Julia Anonymous Functions](https://docs.julialang.org/en/v1/manual/functions/#Anonymous-Functions).
    - G.2.3 Callable Objects  
      Defining call methods on types allows instances to behave like functions via overloading the call operator. This technique attaches behavior directly to objects through zero-argument or multi-argument call definitions. Refer to [Julia Callable Objects](https://docs.julialang.org/en/v1/manual/methods/#Manual-Callable-Objects).
    - G.2.4 Optional Arguments  
      Functions can have optional arguments with default values specified by assignment in the signature, enabling calls with fewer parameters and default fallback behavior. This simplifies function interfaces while maintaining flexibility. See [Julia Optional Arguments](https://docs.julialang.org/en/v1/manual/functions/#Default-Arguments).
    - G.2.5 Keyword Arguments  
      Keyword arguments, introduced by a semicolon in the function signature, allow passing named parameters with defaults. They enhance clarity and allow calling functions with parameters in any order. Details at [Julia Keyword Arguments](https://docs.julialang.org/en/v1/manual/functions/#Keyword-Arguments).
    - G.2.6 Function Overloading  
      Julia selects function implementations based on argument types annotated with ::. Multiple method definitions with the same name but different argument types support polymorphism, with the most specific method applied at runtime. More at [Julia Multiple Dispatch](https://docs.julialang.org/en/v1/manual/methods/#Manual-Multiple-Dispatch).
    - G.2.7 Splatting  
      The ... operator expands the elements of a vector or tuple to be passed as individual arguments to a function. This technique allows flexible argument passing and unpacking in function calls. See [Julia Splatting](https://docs.julialang.org/en/v1/manual/functions/#Function-Arguments).
  - G.3 Control Flow
    - G.3.1 Conditional Evaluation  
      Conditional logic uses if-elseif-else blocks to execute code based on Boolean expressions. The ternary operator provides concise if-else evaluation returning one of two values. Both structures facilitate decision making in code. See [Julia Conditionals](https://docs.julialang.org/en/v1/manual/control-flow/#Conditional-Statements).
    - G.3.2 Loops  
      While loops repeatedly execute code until a condition fails, demonstrated with an example summing an array. For loops iterate over ranges or collections and can use =, in, or ∈ for iterator assignment. Loops support mutable and immutable collections alike. More at [Julia Loops](https://docs.julialang.org/en/v1/manual/control-flow/#Loops).
    - G.3.3 Iterators  
      Iterators enable looping over collections and can be combined or manipulated using functions like enumerate, eachindex, zip, subsets (from IterTools), and product (Cartesian products). The collect function converts these iterators into arrays for inspection. For further reading, see [Julia Iterators](https://docs.julialang.org/en/v1/manual/iteration/).
  - G.4 Packages
    - G.4.1 NamedTupleTools.jl  
      NamedTupleTools.jl offers utilities for creating, merging, selecting, and deleting named tuples, facilitating manipulation and composition of named tuples beyond base Julia functionality. Visit [NamedTupleTools.jl GitHub](https://github.com/JuliaCollections/NamedTupleTools.jl) for details.
    - G.4.2 LightGraphs.jl  
      LightGraphs.jl provides graph data structures and basic operations such as creating directed graphs, adding and removing edges, and querying neighbors and node counts. It supports simple graph algorithms with an intuitive API. See [LightGraphs.jl Documentation](https://juliagraphs.org/LightGraphs.jl/stable/).
    - G.4.3 Distributions.jl  
      Distributions.jl supports creating, sampling from, and fitting probability distributions, including Normal, Multivariate Normal, and Dirichlet. It includes construction of parameters, random sampling, and parameter estimation from data. Refer to [Distributions.jl Documentation](https://juliastats.org/Distributions.jl/stable/).
    - G.4.4 JuMP.jl  
      JuMP.jl is a modeling language for optimization problems allowing variable definition, constraints, and objective functions. It interfaces with solvers like GLPK, supports solution extraction, and provides a high-level syntax for optimization. See [JuMP.jl Documentation](https://jump.dev/JuMP.jl/stable/).
