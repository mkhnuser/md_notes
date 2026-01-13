# Testing

## Fuzzy Testing

Fuzzy testing provides a way to send you app unexpected inputs which can lead to unexpected consequences.

## How do you name tests?

test_<method_name>_<input>_<exprected_result> is the way to name tests:
test_register_user_with_existent_username_throws_exception;
test_increase_balance_with_non_zero_deposit_balance_increased;
test_add_note_with_empty_note_throws_exception;
etc...
