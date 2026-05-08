# FreePACT Reconstructor Plugin for ctapipe

This package provides the **FreePACT** reconstructor as a plugin for the `ctapipe` framework. FreePACT (and its base algorithm ImPACT) is a Monte Carlo template-based image fitting method for Cherenkov telescopes.

## Installation

This package should be installed in the same environment as `ctapipe`.

To install in editable mode:
```bash
pip install -e .
```

## Dependencies

- `ctapipe>=0.17.0`
- `tensorflow` (for neural network based likelihood prediction)
- `iminuit` (for likelihood minimization)
- `astropy`
- `numba`
- `scipy`

## Usage

Once installed, the `FreePACTReconstructor` and `ImPACTReconstructor` are automatically registered with `ctapipe`. You can use them in your Python scripts or configuration files:

```python
from ctapipe.reco import Reconstructor

# The reconstructors will be available in the list of non-abstract subclasses
reco_freepact = Reconstructor.from_name(
    "FreePACTReconstructor",
    subarray=subarray,
    atmosphere_profile=atmosphere_profile
)

reco_impact = Reconstructor.from_name(
    "ImPACTReconstructor",
    subarray=subarray,
    atmosphere_profile=atmosphere_profile
)
```

### Configuration

You can configure the path to the image templates via the `image_template_path` parameter:

```python
reconstructor.image_template_path = "/path/to/your/templates/"
```

## Features

- **ImPACT Algorithm**: Implementation of the likelihood-based image fitting algorithm.
- **Neural Network Templates**: Uses TensorFlow models for fast and accurate image prediction.
- **Plugin Architecture**: Seamless integration with `ctapipe`'s tool and factory systems.

## Development and Testing

Unit tests are provided in `src/freepact_reco/test/`. You can run them using `pytest`:

```bash
pytest src/freepact_reco/test/
```

## References

- [parsons14] Parsons & Hinton, Astroparticle Physics 56 (2014), pp. 26-34
- [schwefer24] Schwefer, Parsons, & Hinton, Astroparticle Physics 163 (2024), 103008
