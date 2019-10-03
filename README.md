# PyXLL Notebook


This project bridges PyXLL and Jupyter Notebooks.

Simply, it enables Excel add-ins to be written in Python using PyXLL, but for the
Python code to be executed in an IPython kernel running on a Jupyter Notebook server.

## Status

This project is currently a proof of concept, and so lots of things are missing.

### What's working

- Excel functions (UDFs):
    Excel functions in a remote Jupyter notebook decorated with @xl_func can be used from Excel in
    the same way as if they were being run locally.

### What's not working yet

- Cached objects
- XLCell arguments
- Macros
- Menus
- Ribbon functions
- RTD functions
- Excel C wrapper functions
- Custom types
- ...probably much more

## Usage

At the moment there is no easy way to login to a secured remote notebook server without making some
code changes.

For testing, use a local notebook server by running jupyter as follows:

```cmd
jupyter notebook
```

You may need to update your PYTHONPATH before running the notebook server so that the pyxll_notebook
package can be found.

Update pyxll-notebook.cfg with the configuration of your local notebook server, including the
auth token that will have been printed out when you ran the above command.

Add pyxll-notebook.cfg as an extenal config to your main pyxll.cfg, and when you start Excel
it will load the notebook specified in the config.

```ini
[PYXLL]
external_config =
    <<path to pyxll-notebook.cfg>>
```

See `examples/test.ipynb` for example usage.

## Requirements

### Client Side (Excel)

- Python, minimum version is 3.6
- PyXLL (www.pyxll.com)
- Microsoft Excel

### Server Side (Jupyter notebook server)

- Python, minimum version is 2.7