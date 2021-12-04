<p align="center">
    <a href="#readme">
        <img width=65% alt="Plotly-Resampler logo" src="docs/_static/logo.png">
    </a>
</p>

[![PyPI Latest Release](https://img.shields.io/pypi/v/plotly-resampler.svg)](https://pypi.org/project/plotly-resampler/)
[![codecov](https://img.shields.io/codecov/c/github/predict-idlab/plotly-resampler?logo=codecov)](https://codecov.io/gh/predict-idlab/plotly-resampler)
[![Code quality](https://img.shields.io/lgtm/grade/python/github/predict-idlab/plotly-resampler?label=code%20quality&logo=lgtm)](https://lgtm.com/projects/g/predict-idlab/plotly-resampler/context:python)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?)](http://makeapullrequest.com)
[![Documentation](https://github.com/predict-idlab/plotly-resampler/actions/workflows/deploy-docs.yml/badge.svg)](https://github.com/predict-idlab/plotly-resampler/actions/workflows/deploy-docs.yml)
[![Testing](https://github.com/predict-idlab/plotly-resampler/actions/workflows/test.yml/badge.svg)](https://github.com/predict-idlab/plotly-resampler/actions/workflows/test.yml)

<!-- [![Downloads](https://pepy.tech/badge/plotly-resampler)](https://pepy.tech/project/plotly-resampler) -->

> `plotly_resampler` enables visualizing large sequential data by **adding resampling functionality to Plotly figures**.

<p align="center">
    <a href="#readme">
        <img width=95% alt="example demo" src="docs/_static/basic_example.gif">
    </a>
</p>

In [this Plotly-Resampler demo](examples/basic_example.ipynb) over `110,000,000` data points are visualized! 

<!-- #### Useful links -->

<!-- - [Documentation]() work in progress 🚧  -->
<!-- - [Example notebooks](https://github.com/predict-idlab/plotly-resampler/tree/main/examples/) -->

### Installation

| [**pip**](https://pypi.org/project/plotly_resampler/) | `pip install plotly-resampler` | 
| ---| ----|
<!-- | [**conda**](https://anaconda.org/conda-forge/plotly_resampler/) | `conda install -c conda-forge plotly_resampler` | -->


## Usage

To **add dynamic resampling to your plotly Figure**, you should;
1. wrap the constructor of your plotly Figure with `FigureResampler`
2. call `.show_dash()` on the Figure

(OPTIONAL) add the trace data as `hf_x` and `hf_y` (for faster initial loading)

### Minimal example

```python
import plotly.graph_objects as go; import numpy as np
from plotly_resampler import FigureResampler

x = np.arange(1_000_000)
noisy_sin = (3 + np.sin(x / 200) + np.random.randn(len(x)) / 10) * x / 1_000

fig = FigureResampler(go.Figure())
fig.add_trace(go.Scattergl(name='noisy sine', showlegend=True), hf_x=x, hf_y=noisy_sin)

fig.show_dash(mode='inline')
```

### Features

* **Convenient** to use:
  * just add the `FigureResampler` decorator around a plotly Figure consructor and call `.show_dash()`
  * allows all other ploty figure construction flexibility to be used!
* **Environment-independent** 
  * can be used in Jupyter, vscode-notebooks, Pycharm-notebooks, as application (on a server)
* Interface for **various downsampling algorithms**:
  * ability to define your preffered sequence aggregation method

<br>

---

<p align="center">
👤 <i>Jonas Van Der Donckt, Jeroen Van Der Donckt, Emiel Deprost</i>
</p>
