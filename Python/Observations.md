# General Observations

## Check whether a string is a number

Use this code if you want to check whether a string is a number:

    str.isnumeric(token.lstrip("+-"))

Plus or minus sign do not count as numbers so the check will fail.
