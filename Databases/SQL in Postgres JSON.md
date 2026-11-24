# SQL in Postgres JSON

## How does one store JSON?

There are multiple ways to store JSON:

* As a `TEXT` column:

      If one wants to just persist JSON blob in a database.
      No JSON field access is allowed.

* `JSON`:

      The option which stores plain-text, unparsted JSON.
      Because of this, the whole JSON document is fast to retrieve and write.

      However, when a JSON field has to be accessed,
      JSON has to be parsed, and so the read latency increases in this case.

      The option doesn't allow to execute some JSON operators: ?, @>.

* `JSONB`:

      The option which parses JSON.
      Duplicate keys will be deleted and keys will possibly be reordered.

      The option allows for a quick JSON field access, since JSON is parsed.
      A GIN index can also be used.

Since `JSONB` is more versatile, one should prefer its usage.

See "Just use Postgres", 5.1 Storing JSON data.

## JSON querying operators

* ->:

      Access JSON field and return it as JSON.

* ->>:

      Access JSON field and return it as TEXT.

* ?:

      See whether a key exists.
      Only JSONB supports this operator.
* @>:

      See whether one JSON object contains another.
      Only JSONB supports this operator.

* JSON path expressions.

See "Just use Postgres", 5.4 Querying JSON data.

## JSON modification

One can modify JSON in two ways:

1. Query JSON, modify it in an application, and then store JSON back:

        The option should be reserved for complex modifications.

2. Modify JSON in a database.

        The option should be used for simple modifications.

See "Just use Postgres", 5.5 Modifying JSON data.
