# PyMallows

A fast implementation of the Mallows model for generating votes and rankings, written in Rust with Python bindings.

## Installation

### Using pip

```bash
# For Intel Mac + Python 3.10
pip install https://github.com/tomonatu8/pymallows/raw/main/wheels/pymallows-0.1.0-cp310-cp310-macosx_10_12_x86_64.whl
# or
rye add pymallows --url https://github.com/tomonatu8/pymallows/raw/main/wheels/pymallows-0.1.0-cp310-cp310-macosx_10_12_x86_64.whl

# For Apple Silicon (M1/M2/M3/M4) + Python 3.10
pip install https://github.com/tomonatu8/pymallows/raw/main/wheels/pymallows-0.1.0-cp310-cp310-macosx_11_0_arm64.whl
# or
rye add pymallows --url https://github.com/tomonatu8/pymallows/raw/main/wheels/pymallows-0.1.0-cp310-cp310-macosx_11_0_arm64.whl
```

## Usage

```python
from mallows import generate_mallows_votes

# Generate 10 votes with 5 candidates
num_candidates = 5
num_voters = 10
phi = 0.5  # dispersion parameter (0 = identical votes, 1 = random votes)
reference_ranking = list(range(num_candidates))  # [0, 1, 2, 3, 4]

# Generate votes
votes = generate_mallows_votes(num_candidates, num_voters, phi, reference_ranking)

# Print the votes
for i, vote in enumerate(votes):
    print(f"Voter {i+1}: {vote}")
```

## Development

### Setup Development Environment

```bash
# Clone the repository
git clone https://github.com/tomonatu8/pymallows.git
cd pymallows
```


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
