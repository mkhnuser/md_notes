# Regular Expressions and Finite State Automata

## Regular Expressions

When you define regular expressions, make sure to specify the order of operator precedence.
Also, if an alphabet includes a special character, make sure to escape one: `\(`.

## The relation between a regular expression and a language

Understand: each reg. exp. defines a language.
In fact, one can view reg. exp. as a concise language definition.
Note: each reg. exp. defines a language, but not each language can be defined by a reg. exp.

## Finite State Machine

FSM, or a Finite State Automaton, is an abstract sequential circuit.
A deterministic FSM accepts an input symbol and its current state and transitions into another state.
A non-deterministic one accepts the current state and an input symbol and might transition into more than one state.
