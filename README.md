<!-- =================================================
# Copyright (c) Facebook, Inc. and its affiliates
Authors  :: Vikash Kumar (vikashplus@gmail.com), Vittorio Caggiano (caggiano@gmail.com)
================================================= -->
<img src="./docs/source/images/Full Color Horizontal wider.png" width=800>

[![Support Ukraine](https://img.shields.io/badge/Support-Ukraine-FFD500?style=flat&labelColor=005BBB)](https://opensource.facebook.com/support-ukraine)
![PyPI](https://img.shields.io/pypi/v/myosuite)
[![Documentation Status](https://readthedocs.org/projects/myosuite/badge/?version=latest)](https://myosuite.readthedocs.io/en/latest/?badge=latest)
![PyPI - License](https://img.shields.io/pypi/l/myosuite)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/facebookresearch/myosuite/blob/main/docs/CONTRIBUTING.md)
[![Downloads](https://pepy.tech/badge/myosuite)](https://pepy.tech/project/myosuite)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1U6vo6Q_rPhDaq6oUMV7EAZRm6s0fD1wn?usp=sharing)

`MyoSuite` is a collection of musculoskeletal environments and tasks simulated with the [MuJoCo](http://www.mujoco.org/) physics engine and wrapped in the OpenAI ``gym`` API to enable the application of Machine Learning to bio-mechanic control problems


Below is an overview of the tasks in the MyoSuite. Full task details are available [here](https://github.com/facebookresearch/myosuite/blob/main/docs/source/suite.rst#tasks), and baseline details are available [here](https://github.com/facebookresearch/myosuite/tree/main/myosuite/agents/baslines_NPG)
<img width="1240" alt="TasksALL" src="./docs/source/images/myoSuite_All.png">


## Getting Started
You will need Python 3.7.1 or later versions. At this moment the library has been tested **only on MacOs and Linux** with [MuJoCo v2.1.0](https://github.com/deepmind/mujoco/releases/tag/2.1.0).

It is recommended to use [Miniconda](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links) and to create a separate environment with
``` bash
conda create --name myosuite python=3.7.1
conda activate myosuite
```

It is possible to install MyoSuite with:
``` bash
pip install -U myosuite
```
for advance installation see [here](setup/README.md).

Test your installation using (this will return also a list of all the current environments):
``` bash
python myosuite/tests/test_myo.py
```

You can also visualize the environments with random controls using the command below:
```
$ python myosuite/utils/examine_env.py --env_name myoElbowPose1D6MRandom-v0
```
**NOTE:** If the visualization results in a GLFW error, this is because `mujoco-py` does not see some graphics drivers correctly. This can usually be fixed by explicitly loading the correct drivers before running the python script. See [this page](setup/README.md#known-issues) for details.

## Examples
It is possible to create and interface with MyoSuite environments like any other OpenAI gym environments. For example, to use the `myoElbowPose1D6MRandom-v0` environment it is possible simply to run: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1U6vo6Q_rPhDaq6oUMV7EAZRm6s0fD1wn?usp=sharing)


```python
import myosuite
import gym
env = gym.make('myoElbowPose1D6MRandom-v0')
env.reset()
for _ in range(1000):
  env.sim.render(mode='window')
  env.step(env.action_space.sample()) # take a random action
env.close()
```



You can find [tutorials](https://github.com/facebookresearch/myosuite/tree/main/docs/source/tutorials#tutorials) on how to load MyoSuite models/tasks, train them and visualize their outcome. Also, you can find [baselines](https://github.com/facebookresearch/myosuite/tree/main/myosuite/agents) to test some pre-trained policies.

## License

MyoSuite is licensed under the [Apache License](LICENSE)

## Citation

If you find this repository useful in your research, please consider giving a star ⭐ and cite it by using the following BibTeX entrys.

<!-- the [arXiv paper](www)  -->

```BibTeX
@Misc{MyoSuite2022,
  author =       {Vittorio, Caggiano AND Huawei, Wang AND Guillaume, Durandau AND Massimo, Sartori AND Vikash, Kumar},
  title =        {MyoSuite: A fast and contact-rich simulation suite for musculoskeletal motor control},
  howpublished = {\url{https://github.com/facebookresearch/myosuite}},
  year =         {2022}
}
```
