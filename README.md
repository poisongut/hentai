<p align="center">
  <img height="150" style="margin-top:15px" src="https://raw.githubusercontent.com/hentai-chan/hentai/master/docs/hentai.svg">
</p>

<p align="center">
  <i>“De gustibus non est disputandum.”</i>
</p>

<p align="center">
    <a href="https://github.com/hentai-chan/hentai/actions?query=workflow%3ACI">
        <img src="https://github.com/hentai-chan/hentai/workflows/CI/badge.svg">
    </a>
    <a href="https://pypi.org/project/hentai/">
        <img src="https://github.com/hentai-chan/hentai/workflows/PyPI/badge.svg">
    </a>
    <img src="https://img.shields.io/pypi/v/hentai?color=blue&label=Release">
    <img src="https://img.shields.io/badge/Python-3.7%20%7C%203.8-blue">
    <a href="https://www.gnu.org/licenses/gpl-3.0.en.html">
        <img src="https://img.shields.io/badge/License-GPLv3-blue.svg">
    </a>
</p>

# Python Hentai API Wrapper

This python package implements a wrapper class around nhentai's RESTful API.
Please be aware that this is not an official API, technical questions about
nhentai.net should be redirected to
[support@nhentai.com](mailto:support@nhentai.com).
Further note that the content of this module is generally considered NSFW. Finally,
I would like to comment at this point that you should under no circumstances use
this module to make an unreasonable amount of requests in a short period of time.

## Installation

Get the most recent stable release from PyPI:

```bash
pip install hentai
```

Alternatively, if you're looking to make a
[contribution](https://github.com/hentai-chan/hentai/blob/dev-hentai/CONTRIBUTING.md)
fork this repository and run

```bash
python -m venv venv/
venv/Scripts/Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements/dev.txt
```

Make sure to checkout `rec-hentai` so that your work is up-to-date with the next
release candidate.

## Basic Usage

`Hentai` makes it very easy to browse through nhentai.net. It implements a flat
namespace for easy access of all their endpoints:

```python
from hentai import Hentai, Format

doujin = Hentai(177013)

# True
Hentai.exists(doujin.id)

# METAMORPHOSIS
print(doujin.title(Format.Pretty))

# [Tag(id=3981, type='artist', name='shindol', url='/artist/shindol/', count=279)]
print(doujin.artist)

# ['dark skin', 'group', ... ]
print([tag.name for tag in doujin.tag])

# 2016-10-18 14:28:49
print(doujin.upload_date)

# ['https://i.nhentai.net/galleries/987560/1.jpg', ... ]
print(doujin.image_urls)

# get the source
doujin.download()
```

Apart from that, `hentai.Utils` also provides a handful of miscellaneous helper
methods:

```python
from hentai import Utils, Sort

print(Utils.get_random_id())

# recommend me something good!
print(Utils.get_random_hentai())

# advanced search with queries
for doujin in Utils.search_by_query('tag:loli', sort=Sort.PopularWeek):
    print(Hentai.get_title(doujin))
```

See also [https://nhentai.net/info/](https://nhentai.net/info/) for more information
on search queries.

## Documentation

I know this is important. I will be working on automating this in a timely manner.
Stay tuned! In the mean time, use the [wiki](https://github.com/hentai-chan/hentai/wiki)
as a first point of reference.

## Get In Touch

You can reach me at [dev.hentai-chan@outlook.com](mailto:dev.hentai-chan@outlook.com)
for private questions and inquires that don't belong to the issue tab.
