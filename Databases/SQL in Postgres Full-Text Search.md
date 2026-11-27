# SQL in Postgres Full-Text Search

## How do you implement a full-text search?

Here is a plan for achieving a full-text search in Postgres:

1. Obtain raw text, which is often called a document.
2. Tokenize the raw text.
3. Normalize the tokenized text into lexemes.

        Use to_tsvector function to obtain lexemes out of a document.

4. Store and index the result of tokenization and normalization in the database.

        Store the result of a to_tsvector function invocation on a document
        in a separate table column.

5. Perform a full-text search.

        A search query has to be broken down into lexemes as well.
        For this, the query has to be transformed into tsquery.

6. Rank the search results.

        See ts_rank and ts_rank_cd functions for this.
        You might rank by how many times a query lexeme is present in text lexemes.
        A weight-based ranking is also possible:
        for example, a name column might take priority over a description column.

See "Just use Postgres", 6.1 Basics of full-text search in Postgres.
See "Just use Postgres", 6.3 Performing full-text search
See "Just use Postgres", 6.4 Ranking search results.
See "Just use Postgres", 6.6 Indexing lexemes.

## Preprocessing example

An example: suppose a sentence "I am looking outside of the window." is given.

Here is roughly how the preprocessing is going to happen:

1. The document is "I am looking outside of the window.".
2. Obtained tokens are: "I", "am", "looking", "outside", "of", "the", "window", ".".
3. Normalized tokens are: "look", "outsid", "window".

        The prepositions and the punctuation are removed.
        The text stemming is applied.
        The text becomes case-insensitive.

See "Just use Postgres", 6.1 Basics of full-text search in Postgres.

## pg_search extension

Consider the `pg_search` extension for a suite of functions used to a full-text search.
