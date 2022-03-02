[![Documentation Status](https://readthedocs.org/projects/emg-docs/badge/?version=latest)](https://emg-docs.readthedocs.io/en/latest/?badge=latest)

# Documentation for [MGnify: the EBI Metagenomics resource](https://www.ebi.ac.uk/metagenomics)

This repository contains the **source** of MGnify’s documentation.

The readable documentation is hosted [on ReadTheDocs](https://emg-docs.readthedocs.io/en/latest/).

# Issues
We welcome suggestions for and issues with the documentation as [GitHub Issues](https://github.com/EBI-Metagenomics/EMG-docs/issues).

For questions about MGnify itself, please [contact us via the EBI Helpdesk](https://www.ebi.ac.uk/support/metagenomics).

# Developing the documentation
Check out this repository.

You can use `sphinx-autobuild` to watch the `docs/` folder for changes as you save files, rebuild the documentation, and serve it with a local web server.

```shell
# (optionally set up a virtual environment or conda environment)

pip install -r requirements-dev.txt
sphinx-autobuild docs docs/_build/html
```

Browse to [the local webserver](http://127.0.0.1:8000)

The [Sphinx RST Documentation](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html) is a good place to start if you are not familiar with RST syntax.