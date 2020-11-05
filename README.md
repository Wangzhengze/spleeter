<img src="https://github.com/deezer/spleeter/raw/master/images/spleeter_logo.png" height="80" />

[![Github actions](https://github.com/deezer/spleeter/workflows/pytest/badge.svg)](https://github.com/deezer/spleeter/actions) ![PyPI - Python Version](https://img.shields.io/pypi/pyversions/spleeter) [![PyPI version](https://badge.fury.io/py/spleeter.svg)](https://badge.fury.io/py/spleeter) [![Conda](https://img.shields.io/conda/vn/conda-forge/spleeter)](https://anaconda.org/conda-forge/spleeter) [![Docker Pulls](https://img.shields.io/docker/pulls/researchdeezer/spleeter)](https://hub.docker.com/r/researchdeezer/spleeter) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/deezer/spleeter/blob/master/spleeter.ipynb) [![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/spleeter/community) [![status](https://joss.theoj.org/papers/259e5efe669945a343bad6eccb89018b/status.svg)](https://joss.theoj.org/papers/259e5efe669945a343bad6eccb89018b)

## About

**Spleeter** is [Deezer](https://www.deezer.com/) source separation library with pretrained models
written in [Python](https://www.python.org/) and uses [Tensorflow](https://tensorflow.org/). It makes it easy
to train source separation model (assuming you have a dataset of isolated sources), and provides
already trained state of the art model for performing various flavour of separation :

这很容易训练源分离模型（假设您具有隔离源的数据集），并提供已经训练有素的模型可以执行各种分离操作：

* Vocals (singing voice) / accompaniment separation ([2 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-2stems-model))  人声/伴奏声
* Vocals / drums / bass / other separation ([4 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-4stems-model)) 人声/鼓/低音/其他分离
* Vocals / drums / bass / piano / other separation ([5 stems](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-5stems-model))  人声/鼓/贝斯/钢琴/其他分离

2 stems and 4 stems models have [high performances](https://github.com/deezer/spleeter/wiki/Separation-Performances) on the [musdb](https://sigsep.github.io/datasets/musdb.html) dataset. **Spleeter** is also very fast as it can perform separation of audio files to 4 stems 100x faster than real-time when run on a GPU.

Spleeter也非常快，因为它可以在GPU上运行时将音频文件分离为4个stem，比实时快100倍。

We designed  so you can use it straight from [command line](https://github.com/deezer/spleeter/wiki/2.-Getting-started#usage)as well as directly in your own development pipeline as a [Python library](https://github.com/deezer/spleeter/wiki/4.-API-Reference#separator). It can be installed with [Conda](https://github.com/deezer/spleeter/wiki/1.-Installation#using-conda),   with [pip](https://github.com/deezer/spleeter/wiki/1.-Installation#using-pip) or be used with[Docker](https://github.com/deezer/spleeter/wiki/2.-Getting-started#using-docker-image).

可以直接用命令行操作 或者使用python操作  可以再conda下载或者用Pip下载

### Projects and Softwares using **Spleeter**

Since it's been released, there are multiple forks exposing **Spleeter** through either a Guided User Interface (GUI) or a standalone free or paying website. Please note that we do not host, maintain or directly support any of these initiatives.

自发布以来，已有多个分支通过引导用户界面（GUI）或独立的免费或付费网站公开 Spleeter 。请注意，我们不主持，维护或直接支持任何这些举措。

That being said, many cool projects have been built on top of ours. Notably the porting to the *Ableton Live* ecosystem through the [Spleeter 4 Max](https://github.com/diracdeltas/spleeter4max#spleeter-for-max) project.

话虽如此，许多很酷的项目已经建立在我们的基础之上。尤其是通过Spleeter 4 Max项目移植到Ableton Live生态系统。

**Spleeter** pre-trained models have also been used by professionnal audio softwares. Here's a non-exhaustive list:

** Spleeter **预先训练的模型也已被专业音频软件使用。以下是非详尽清单：

* [iZotope](https://www.izotope.com/en/shop/rx-8-standard.html) in its *Music Rebalance* feature within **RX 8**
* [SpectralLayers](https://new.steinberg.net/spectralayers/) in its *Unmix* feature in **SpectralLayers 7**
* [Acon Digital](https://acondigital.com/products/acoustica-audio-editor/) within **Acoustica 7**
* [VirtualDJ](https://www.virtualdj.com/stems/) in their stem isolation feature
* [Algoriddim](https://www.algoriddim.com/apps) in their **NeuralMix** and **djayPRO** app suite

## Quick start

可以使用[Google Colab](https://colab.research.google.com/github/deezer/spleeter/blob/master/spleeter.ipynb).测试

Ready to dig into it ? In a few lines you can install **Spleeter** using [Conda](https://github.com/deezer/spleeter/wiki/1.-Installation#using-conda) and separate the vocal and accompaniment parts from an example audio file:

准备深入研究吗？在几行中，您可以使用[Conda]（https://github.com/deezer/spleeter/wiki/1.-Installation#using-conda）安装** Spleeter **，并从示例中分离人声和伴奏部分音频文件：

```bash
# install using conda
conda install -c conda-forge spleeter
# download an example audio file (if you don't have wget, use another tool for downloading)
wget https://github.com/deezer/spleeter/raw/master/audio_example.mp3
# separate the example audio into two components
spleeter separate -i audio_example.mp3 -p spleeter:2stems -o output
```

You should get two separated audio files (`vocals.wav` and `accompaniment.wav`) in the `output/audio_example` folder.

For a detailed documentation, please check the [repository wiki](https://github.com/deezer/spleeter/wiki)

您应该在`output / audio_example`文件夹中获得两个分开的音频文件（vocals.wav和accompaniment.wav）。

有关详细文档，请查看[repository wiki](https://github.com/deezer/spleeter/wiki)

## Development and Testing

The following set of commands will clone this repository, create a virtual environment provisioned with the dependencies and run the tests (will take a few minutes):

以下命令集将克隆此存储库，创建带有依赖项的虚拟环境并运行测试（将花费几分钟）：

```bash
git clone https://github.com/Deezer/spleeter && cd spleeter
python -m venv spleeterenv && source spleeterenv/bin/activate
pip install . && pip install pytest pytest-xdist
make test
```

## Reference

* Deezer Research - Source Separation Engine Story - deezer.io blog post:
  * [English version](https://deezer.io/releasing-spleeter-deezer-r-d-source-separation-engine-2b88985e797e)
  * [Japanese version](http://dzr.fm/splitterjp)
* [Music Source Separation tool with pre-trained models / ISMIR2019 extended abstract](http://archives.ismir.net/ismir2019/latebreaking/000036.pdf)

If you use **Spleeter** in your work, please cite:

如果您在工作中使用** Spleeter **，请引用：

```BibTeX
@article{spleeter2020,
  doi = {10.21105/joss.02154},
  url = {https://doi.org/10.21105/joss.02154},
  year = {2020},
  publisher = {The Open Journal},
  volume = {5},
  number = {50},
  pages = {2154},
  author = {Romain Hennequin and Anis Khlif and Felix Voituret and Manuel Moussallam},
  title = {Spleeter: a fast and efficient music source separation tool with pre-trained models},
  journal = {Journal of Open Source Software},
  note = {Deezer Research}
}
```

## License

The code of **Spleeter** is [MIT-licensed](LICENSE).

## Disclaimer

If you plan to use **Spleeter** on copyrighted material, make sure you get proper authorization from right owners beforehand.

如果您打算在受版权保护的材料上使用** Spleeter **，请确保事先获得权利所有者的适当授权。

## Troubleshooting

**Spleeter** is a complex piece of software and although we continously try to improve and test it you may encounter unexpected issues running it. If that's the case please check the [FAQ page](https://github.com/deezer/spleeter/wiki/5.-FAQ) first as well as the list of [currently open issues](https://github.com/deezer/spleeter/issues)  

** Spleeter **是一个复杂的软件，尽管我们不断尝试改进和测试它，但您可能会在运行它时遇到意外问题。如果是这种情况，请先检查[FAQ page](https://github.com/deezer/spleeter/wiki/5.-FAQ)以及[currently open issues](https://github.com/deezer/spleeter/issues)

### Windows users

   It appears that sometimes the shortcut command `spleeter` does not work properly on windows. This is a known issue that we will hopefully fix soon. In the meantime replace `spleeter separate` by `python -m spleeter separate` in command line and it should work.

似乎有时快捷方式命令`spleeter`在Windows上无法正常工作。这是一个已知问题，我们很快会解决。同时，在命令行中用`python -m spleeter`独立的替换`spleeter separate`，它应该可以工作。

## Contributing

If you would like to participate in the development of **Spleeter** you are more than welcome to do so. Don't hesitate to throw us a pull request and we'll do our best to examine it quickly. Please check out our [guidelines](.github/CONTRIBUTING.md) first.

如果您想参与** Spleeter **的开发，我们将非常欢迎您。不要犹豫，向我们提出请求，我们将竭尽所能，以快速进行检查。请先查看我们的[guidelines](.github/CONTRIBUTING.md)

## Note

This repository include a demo audio file `audio_example.mp3` which is an excerpt
from Slow Motion Dream by Steven M Bryant (c) copyright 2011 Licensed under a Creative
Commons Attribution (3.0) [license](http://dig.ccmixter.org/files/stevieb357/34740)
Ft: CSoul,Alex Beroza & Robert Siekawitch

该存储库包含一个演示音频文件“ audio_example.mp3”，该文件是摘录
摘自Steven M Bryant的《慢动作梦》（c）版权所有2011
共同点归属（3.0）[许可]（