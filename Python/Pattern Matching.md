# Pattern Matching

## Pattern Matching and Enums

Pattern Matching can be powerfully combined with Enums:

```
from enum import Enum

DocFormat = Enum("DocFormat", ["PDF", "TXT", "MD", "HTML"])

def convert(content, from_format, to_format):
    match (from_format, to_format):
        case (DocFormat.MD, DocFormat.HTML):
            content = content.replace("# ", "<h1>")
            return content + "</h1>"
        case (DocFormat.TXT, DocFormat.PDF):
            return f"[PDF] {content} [PDF]"
        case (DocFormat.HTML, DocFormat.MD):
            content = content.replace("<h1>", "# ")
            return content.replace("</h1>", "")
        case _:
            raise Exception("invalid type")
```
