```markdown
# openpilot Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns and conventions used in the openpilot repository, a Python-based codebase with no detected framework. You'll learn file naming, import/export styles, commit conventions, and how to write and run tests. This guide also provides suggested commands for common workflows to streamline your development process.

## Coding Conventions

### File Naming
- **Style:** camelCase
- **Example:**  
  ```python
  myModule.py
  vehicleInterface.py
  ```

### Import Style
- **Style:** Relative imports
- **Example:**  
  ```python
  from .utils import calculateSpeed
  from ..common import logger
  ```

### Export Style
- **Style:** Named exports (explicitly listing what is exported)
- **Example:**  
  ```python
  __all__ = ['VehicleInterface', 'calculateSpeed']
  ```

### Commit Patterns
- **Type:** Freeform messages, sometimes prefixed
- **Prefixes:** `[bot]`, `webrtc`
- **Average Length:** ~42 characters
- **Example:**  
  ```
  [bot] update submodules for release
  webrtc: improve connection stability
  fix lane detection edge case
  ```

## Workflows

### Code Contribution
**Trigger:** When adding new features or fixing bugs  
**Command:** `/contribute`

1. Create a new branch for your feature or fix.
2. Follow camelCase naming for new files.
3. Use relative imports for modules.
4. Explicitly declare exports using `__all__` if needed.
5. Write or update tests in files matching `*.test.*`.
6. Commit changes with a descriptive message, optionally using `[bot]` or `webrtc` prefixes.
7. Open a pull request for review.

### Testing Code
**Trigger:** Before merging or after making changes  
**Command:** `/test`

1. Identify or create test files matching the pattern `*.test.*`.
2. Write test cases for new or modified code.
3. Run the test suite using the project's preferred method (framework unknown; check project docs or use `python -m unittest` as a fallback).
4. Ensure all tests pass before submitting changes.

## Testing Patterns

- **Test File Pattern:** `*.test.*` (e.g., `vehicleInterface.test.py`)
- **Framework:** Unknown (check project documentation)
- **Example Test File:**  
  ```python
  # vehicleInterface.test.py
  import unittest
  from .vehicleInterface import VehicleInterface

  class TestVehicleInterface(unittest.TestCase):
      def test_speed_calculation(self):
          vi = VehicleInterface()
          self.assertEqual(vi.calculateSpeed(10, 2), 5)

  if __name__ == '__main__':
      unittest.main()
  ```

## Commands
| Command      | Purpose                                 |
|--------------|-----------------------------------------|
| /contribute  | Guide for contributing code             |
| /test        | Steps for running and writing tests     |
```
