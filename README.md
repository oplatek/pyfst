# pyfst

Python interface to [OpenFst](http://openfst.org)

Documentation: http://pyfst.github.io

## Installation

1. Install OpenFst 1.3
2. Build the fork using `setup.py`

```bash
# Change for your setting needed only if openfst is not in PYTHONPATH
export FST=/ha/work/people/oplatek/kaldi/tools/openfst  
LIBRARY_PATH=$FST/lib:$FST/lib/fst CPLUS_INCLUDE_PATH=$FST/include python setup.py build_ext --inplace
#for further usage
export LD_LIBRARY_PATH=$FST/lib:$FST/lib/fst:$LD_LIBRARY_PATH
```

## Basic Usage

```python
import fst

t = fst.Transducer()

t.add_arc(0, 1, 'a', 'A', 0.5)
t.add_arc(0, 1, 'b', 'B', 1.5)
t.add_arc(1, 2, 'c', 'C', 2.5)

t[2].final = 3.5

t.shortest_path() # 2 -(a:A/0.5)-> 1 -(c:C/2.5)-> 0/3.5 
```

The pyfst API is [IPython notebook](http://ipython.org/ipython-doc/dev/interactive/htmlnotebook.html)-friendly: the transducers objects are [automatically drawn](http://nbviewer.ipython.org/3835477/) using [Graphviz](http://www.graphviz.org).

## Development

See [the wiki](https://github.com/vchahun/pyfst/wiki/Contributing) to learn about how to install pyfst from the Cython source.

## License

Copyright 2013 Victor Chahuneau

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
