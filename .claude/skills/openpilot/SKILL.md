```markdown
# openpilot Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns, coding conventions, and common workflows for contributing to the openpilot codebase. openpilot is primarily written in Python, with some C++ components for performance-critical modules such as video encoding and logging. The repository emphasizes modularity, clear file organization, and a pragmatic approach to testing and workflow automation.

## Coding Conventions

### File Naming
- Use **snake_case** for Python files and modules.
  - Example: `athenad.py`, `test_athenad.py`
- C++ files use lower case with underscores.
  - Example: `v4l_decoder.cc`, `clip_encoder.h`

### Import Style
- Prefer **relative imports** within Python packages.
  - Example:
    ```python
    from .utils import some_helper
    ```

### Export Style
- Use **named exports** (explicit function/class definitions).
  - Example:
    ```python
    def process_event(event):
        ...
    ```

### Commit Patterns
- Commit messages are freeform but often start with a relevant prefix (e.g., `loggerd:`, `clips:`, `encoderd:`, `athena:`).
- Keep commit messages concise (average ~35 characters).
  - Example: `loggerd: fix frame timestamp bug`

## Workflows

### athenad-feature-or-fix-workflow
**Trigger:** When you want to add a new feature or fix a bug in `athenad.py`  
**Command:** `/athenad-feature`

1. Edit or extend `openpilot/system/athena/athenad.py` to implement the feature or fix.
2. If applicable, update or add tests in `openpilot/system/athena/tests/test_athenad.py`.

**Example:**
```python
# openpilot/system/athena/athenad.py
def new_feature():
    # implementation here
    pass
```
```python
# openpilot/system/athena/tests/test_athenad.py
def test_new_feature():
    assert new_feature() == expected_result
```

### loggerd-encoder-pipeline-update
**Trigger:** When you want to add or refactor video encoding/decoding/transcoding functionality in loggerd  
**Command:** `/loggerd-encoder-update`

1. Edit or add C++ source/header files in `openpilot/system/loggerd/encoder/` (e.g., `v4l_decoder.cc`, `v4l_encoder.h`).
2. Edit or add related files in `openpilot/system/loggerd/` (e.g., `clip_encoder.cc`, `encoderd.cc`, `video_writer.cc`).
3. Update build scripts (`SConscript`) as needed.
4. If applicable, update `tools/replay/` files for replay support.

**Example:**
```cpp
// openpilot/system/loggerd/encoder/v4l_encoder.cc
#include "v4l_encoder.h"

void V4LEncoder::Encode(const Frame &frame) {
  // encoding logic
}
```
```python
# Update SConscript
env.Program('v4l_encoder', ['v4l_encoder.cc'])
```

## Testing Patterns

- Test files are named with the pattern `*.test.*` (e.g., `test_athenad.py`).
- The testing framework is not explicitly stated; tests are typically written as Python functions.
- Place tests in a `tests/` subdirectory next to the module under test.
  - Example: `openpilot/system/athena/tests/test_athenad.py`

**Example:**
```python
def test_functionality():
    result = function_under_test()
    assert result == expected
```

## Commands
| Command                 | Purpose                                                        |
|-------------------------|----------------------------------------------------------------|
| /athenad-feature        | Start a feature or bugfix workflow for `athenad.py`            |
| /loggerd-encoder-update | Begin an update to the loggerd encoder/decoder pipeline        |
```
