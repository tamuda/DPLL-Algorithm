SAT Solver using DPLL Algorithm 
(Quicknote: I initially created this as a python file and used chmod to make it an executable, so it should be able to run with ./sat)

This SAT solver implements the DPLL algorithm to determine the satisfiability of propositional logic formulas in CNF. The solver includes the following features:

Backtracking Search
Early Termination
Unit Clause Heuristic
Pure Literal Heuristic

The program reads an input formula from standard input file and outputs whether the formula is satisfiable. If satisfiable, it provides a variable assignment that satisfies the formula.

Usage:
python ./sat.py < input

Options:
--nounit: Disable unit clause heuristic.
--nopure: Disable pure literal heuristic.

Input Format:
The input formula should be in cnf with variables represented as integers. Each clause is a list of literals separated by spaces, and each clause is separated by a newline. Negation indicated by a squiggly sign (~).

Example Input:
A,B,C
~A,~B
~A,~C
~B,~C

Implementation Organization
- Main Function: Parses command-line options (--nounit, --nopure), reads the CNF input, initializes data structures, and starts the DPLL algorithm.
- Input Parsing (parse_input): Reads clauses and variables from standard input./
- DPLL Algorithm: Recursively attempts to find a satisfying assignment using heuristics and backtracking (backbone of the project)

Heuristics:
- Unit Clause Heuristic (unit_clause_heuristic): Assigns values to variables appearing in unit clauses.
- Pure Literal Heuristic (pure_literal_heuristic): Assigns values to variables that are pure literals


Additional:
- Simplification (simplify_clauses): Updates the formula based on current assignments, removing satisfied clauses and false literals.
- Variable Selection (select_unassigned_variable): Picks the next variable
- Result Output (print_result): Prints whether the formula is satisfiable and the variable assignments if it is.

Some Benefits of the Heuristics

Unit Clause Heuristic
- Immediate Assignment: Forces a variable to a specific value, this simplifies the formula.
- Reduces Search Space: Eliminates the need to explore alternative assignments for that variable
- Early Conflict Detection: Identifies contradictions sooner, allowing quicker backtracking

Pure Literal Heuristic
- Simplifies Formula: Assigning a pure literal its corresponding value satisfies all clauses containing it.
- Reduces Complexity: Removes clauses from the formula, making it smaller and easier to solve.
- Avoids Unnecessary Assignments: Decreases the number of variables needing exploration.

PS: The heuristics improve the solver's efficiency by simplifying the formula before deeper recursive searches, leading to faster solutions and reduced computational effort.