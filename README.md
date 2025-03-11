# PyMallows

A fast implementation of the Mallows model for generating votes and rankings, written in Rust with Python bindings.

## Installation

### Using pip / rye

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

## Mallows Model
In the Mallows model, the probability of generating a ranking $\pi$ given a reference ranking $\tau$ and a dispersion parameter $\phi \in (0,1]$ is given by

$$
    \Pr[\pi \mid \tau, \phi] = \frac{\phi^{d(\pi,\tau)}}{Z(\phi)},
$$

where $d(\pi,\tau)$ is the Kendall tau distance between $\pi$ and $\tau$, and $Z(\phi)$ is a normalization constant.

As $\phi$ approaches $0$, all probability mass concentrates on the reference ranking $\tau$. As $\phi$ approaches $1$, the distribution becomes uniform over all rankings.

## Development

### Setup Development Environment

```bash
git clone https://github.com/tomonatu8/pymallows.git
cd pymallows
```

## References
- Mallows, C. L. (1957). Non-null ranking models. *Biometrika*, 44(1-2), 114–130.
- Mattei N., and Walsh T. (2013). PrefLib: A library of preference data. In *Proceedings of the 3rd International Conference on Algorithmic Decision Theory (ADT 2013)*.


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
