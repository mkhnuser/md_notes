# Builtins

## Overview

These notes highlight useful builtins.

* `zip` & `zip_longest`;
* `reversed`:

      Implement __reversed__ dunder,
      or provide an object whose size can be determined.

* `open`:

      By default, files are open in a universal newline mode.
      Possible open flags:
            r, w, a;
            r+ or w+ - both reading and writing;
            x - exclusive access.

* `memoryview`:

      MemoryView allows you to create a slice of a buffer without copying.
      Any further modification of the obtained memory view will modify the original buffer.
