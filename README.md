# Rolling Token Authentication

## Usage

### Initialization
```python
from rolling_token_auth import RollingTokenManager

manager = RollingTokenManager("secret", interval=3600)
```
The `interval` defines how long a token is valid in seconds. Shorter = more secure.
Both `secret` and `interval` must match between generation and verification.

### Generation
```python
manager.generate_token()
```
This generates a token for the current timestamp. Optionally a `offset` can be declared.


## Verification
```python
manager.is_valid(token)
```
This checks if the given token is valid for the current timestamp. The `manager.tolerance` parameter defines how many token from the past and future are still valid (default: 1 in each direction).


## Important
- `RollingTokenManager` isn't thread-safe when validating tokens due to its caching behaviour. Use separate instances for each thread.
