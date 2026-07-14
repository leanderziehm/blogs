# Python Language Features

modules are not allowed to start with numbers as they must be valid identifiers

## Language Features:

Constructors:

```
def __init__(self,parameters): ## useful for attribute initialization

def __new__(cls,parameters): ## useful for singeltons
```

Literals:

```
from typing import Literal

AutocompleteType = Literal["save", "delete"]
```

