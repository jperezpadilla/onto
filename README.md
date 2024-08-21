# onto

This is a lightweight replacement for the obsolete OntoManager.

By running ``python onto.py``, all models in the ``models/in`` folder will be re-rendered, and written to the ``models/out`` folder.

Using ``git status`` or ``gitk`` it's easy to see the changes to the generated files, that were applied by the script.

To understand the logging better:
- "Creating" means that the Python objects (representing a function block, a variable, ...) are created, as the yaml files are being parsed.
- "Rendering" means that the Mako files are being executed, using the previously created Python objects
- "Writing" means that the rendering is done to memory, and the files are now being written to disk.


## How to install and run globally

```bash
$ pip3 install mako
$ pip3 install pyyaml
$ python3 onto.py
```

## How to install and run in a virtual environment

Install: 
```bash
$ python3 -m venv .venv
$ source .venv/bin/activate
$ pip3 install mako
$ pip3 install pyyaml
```

Run: 
```bash
$ source .venv/bin/activate
$ python3 onto.py
```

## Tips and tricks

- Currently rendering all models takes less than 1 minute. If it takes longer, something is wrong with the models!
  To make rendering faster, consider to:
   - add 'expand: false'
   - instead of specifying the 'type' of an instance, add the instance manually with 'arguments' and 'attributes' (see existing code)
- Templates starting with an underscore will not be rendered. Use this to "disable" a template, or to make a template that only
  holds helper functions.
- In case of errors, you may want to run the script in VERBOSE mode by running ``python3 onto.py -v``. This will be much slower and 
  will output lot's of ugly low-level log messages. Not for the faint of heart!