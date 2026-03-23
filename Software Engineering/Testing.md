# Testing

## Fuzzy Testing

Fuzzy testing provides a way to send you app unexpected inputs which can lead to unexpected consequences.

## How do you name tests?

test_<method_name>_<input>_<exprected_result> is the way to name tests:
test_register_user_with_existent_username_throws_exception;
test_increase_balance_with_non_zero_deposit_balance_increased;
test_add_note_with_empty_note_throws_exception;
etc...

## Hypothesized Testing

Python's `hypothesis` package, for example, creates hypothesized inputs for your tests.
An advantage compared to randomized testing is that you obtain a minimum counterexample.

## Testing External API

There are several strategies to test an external API:

* Run tests against an actual API (think twice!);
* Create Mock Objects;
* Record and replay the API interaction: see `pytest-vcr` in Python, for an example.
