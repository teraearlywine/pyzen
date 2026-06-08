# Chapter 1: Pythonic Thinking


+ item 1: know what version of python you're using `python3 --version`
+ item 2: follow the pep-8 style guide (pep=python enhancement proposal #8)
    + whitespace matters; 79 spaces or less 
    + naming matters
        + functions, variables and attributes should be in snake_case
        + protected instance attributes should use _leading_underscores 
        + private instance attributes should use __double_leading_underscores 
        + classes should be in CamelCase format 
        + module level constants should be in ALL_CAPS 
        + instance methods in classes should use self which refers to the object as the name of the first parameter
        + class methods should use class which refers to the class as the name of the first parameter
    + organization & importing matters
        + always put import statements at the top of the file 
        + imports should be in sections in the following order; standard library modules, third-party modules, your own modues (last)
        + each sub-section should have imports in alphabetical order 
    + black is the pep-8 standard for automatic formatting & is an official python software foundation project 
        + `pip3 install black` 
        + `python -m black example.py` 
+ item 3: never expect python to detect errors at compile time 
    + python defers nearly all error checking until runtime, incl. detection of problems that seem obvious 
    + community projects like linters & static analysis tools can help catch some of the more common source errors before the program executes
+ item 4: write helper functions instead of complex expressions 
    + pythons syntax makes it too easy to write single line expressions that are overly complicated and difficult to read 
    + move complex expressions into helper functions, especially if you need to reuse the same logic repeatedly. 
+ item 5: prefer multiple-assignment unpacking over indexing
    + python has a built in tuple type that can be used to create immutable, ordered sequences of values (relates to item 56: prefer dataclasses for creating immutable objects)
    + tuples can be empty, contain a single item or contain multiple items;
    + members can be accessed through numerical indexes & slices just like in a list;
        ```python 
        item = ('peanut butter', 'jelly')
        first_item = item[0]  # index
        first_half = item[:0] # slice
        ```
    + python also has syntax for unpacking tuples which allows for assigning multiple values in a single tatement 
        ```python 
        item = ('peanut butter', 'jelly')
        first, second = item
        print(first)
        print(second) 
        ```

    + python special syntax called unpacking for assigning multiple values in a single statement
    + unpacking is generalized in python and can be applied to any iterable including many levels of iterables within iterables 
    + you can reduce visual noice & increase code clarity by using unpacking to avoid explicitly indexing into sequences
+ item 6: always surround single element tuples with parentheses
    + there are 4 kinds of tuple literale values 
        + `first = (1,2,3)`
        + `second = (1,2,3,)` -> has an optional trailing comma
        + 3 & 4 are the same without parentheses. just stick to parentheses
+ item 7: consider conditional expressions (aka ternary expressions) for simple inline logic 
    + python "if" statements are not expressions
    + if, elif and else blocks can all contain additional statements. 
    + e.g. the whole group of blocks doesn't need to evaluate to a single value that can be stored in a variable or passed as a function argument 
    + python supports conditional expressions which let you add if/elif/else nearly anywhere an expression is allowd
        + conditional expressions are basically just one line 
        + i.e. `condition if true value else false value`
    + conditional expr in python allow you to put an if statement anywhere an expression would normally go
    + the order of the test expression, true result expression, and false result expression in a conditional exp. is different than other ternary operators in other languages 
    + don't use cond. expr. in places where they increase ambiguity or harm readability for new code readers
    + prefer standard if statements + helper functions when it's unclear whether conditional statements provide a compelling benefit 
