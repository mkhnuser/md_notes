# Testing

## How do you test with a database?

Consider the usage of an in-memory sqlite database.

## Hypothesized Testing

Python's `hypothesis` package, for example, creates hypothesized inputs for your tests.
An advantage compared to randomized testing is that you obtain a minimum counterexample.

## Testing External API

There are several strategies to test an external API:

* Run tests against an actual API (think twice!);
* Create Mock Objects;
* Record and replay the API interaction: see `pytest-vcr` in Python, for an example.

## Fuzzy Testing

Fuzzy testing provides a way to send you app unexpected inputs which can lead to unexpected consequences.
