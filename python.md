### Type Hints

sets type of a variable

name: str, user: User

from typing import Optional

age: Optional[int]: None

-> same as age: Union[int, None]

-> sets type of variable to int or None

age: Optional[int]:None = None -> type of age can be int or None, with default value = None

---

### Virtual Environments

**python3 -m venv myvenv**: creates a virtual environment named 'myvenv'

**source myvenv/bin/activate**: activates the virtual environment

**deactivate**: deactivates the venv

**rm -rf myvenv**: deletes the venv


### Misc

pip show <library> # Shows the current installed version of a library

