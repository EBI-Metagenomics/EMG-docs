.. _restapi:

RESTful API
===========

With the rapid expansion in the number of datasets deposited in EBI
Metagenomics, it has become increasingly important to provide programmatic
access to the data for cross-database complex queries.


--------
Overview
--------


Current version
^^^^^^^^^^^^^^^

Current API version is **v0.3**

.. note::

    API is under development and any endpoint can change without notice until
    stable version 1 is released


Base URL
^^^^^^^^

The base address to the API is https://www.ebi.ac.uk/metagenomics/api/latest/.

A GET request can be issued to the root endpoint to get all categories that the API supports.

.. highlight:: bash

::

    curl -X GET "https://www.ebi.ac.uk/metagenomics/api/latest/"


There are several easy-to-use top-levels resources, such as
:term:`studies<study>`, :term:`samples<sample>`, :term:`runs<run>`,
experiment-types, :term:`biomes<biome>`, and annotations. For example
https://www.ebi.ac.uk/metagenomics/api/latest/studies retrieves a list
of all studies, while https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004
retrieves a single study, with the accession ERP009004. The samples contained
within this study can be retrieved using the relationship URL:
https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004/samples.


HTTP methods
^^^^^^^^^^^^

API provides read-only access to all resources, that means only HTTP GET
method can be used with expetion of authentication endpoint.


Response
^^^^^^^^

Links to a resource return a JSON object formatted data structure that
contains the resource type (in this example :term:`biomes<biome>`), associated
object identifier (*id*) and *attributes*. Where appropriate, *relationships*
and links are provided to other resources, allowing complex queries to be
constructed.

.. highlight:: json

::

    {
      "data": {
        "type": "studies",
        "id": "ERP009004",
        "attributes": {
          "samples-count": 57,
          "runs-count": 57,
          "accession": "ERP009004",
          "centre-name": "Genome Alberta",
          "public-release-date": null,
          "study-abstract": "Metagenomics for Greener Production and Extraction of Hydrocarbon Energy:\nCreating Opportunities for Enhanced Recovery with Reduced Environmental Impact",
          "study-name": "Hydrocarbon Metagenomics Project",
          "data-origination": "SUBMITTED",
          "last-update": "2016-01-20T14:12:06Z",
          "project-id": "PRJEB7983"
        },
        "relationships": {
          "biomes": {
            "data": [
              {
                "type": "biomes",
                "id": "root:Environmental:Aquatic:Freshwater",
                "links": {
                  "self": "https://www.ebi.ac.uk/metagenomics/api/latest/biomes/root:Environmental:Aquatic:Freshwater"
                }
              },
              {
                "type": "biomes",
                "id": "root:Environmental:Aquatic:Marine",
                "links": {
                  "self": "https://www.ebi.ac.uk/metagenomics/api/latest/biomes/root:Environmental:Aquatic:Marine"
                }
              },
              {
                "type": "biomes",
                "id": "root:Environmental:Terrestrial:Soil",
                "links": {
                  "self": "https://www.ebi.ac.uk/metagenomics/api/latest/biomes/root:Environmental:Terrestrial:Soil"
                }
              }
            ],
            "links": {
              "related": "https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004/biomes"
            },
            "meta": {
              "count": 3
            }
          },
          "publications": {
            "links": {
              "related": "https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004/publications"
            }
          },
          "samples": {
            "links": {
              "related": "https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004/samples"
            }
          }
        },
        "links": {
          "self": "https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP009004"
        }
      }
    }


Hypermedia
^^^^^^^^^^

All resources may have one or more **links** properties referencing to other
resources, to provide explicit URLs so that proper API clients don't need to
construct URLs on their own.

.. note::

    It is highly recommended for API clients to use links for future upgrades
    of the API.


Pagination
^^^^^^^^^^

As some queries can result in a large response, the API supports pagination,
using a page number and size of results per page as query parameters. Request
that return multiple items is paginated to 20 items by default, and can be
increased up to 100:

.. highlight:: bash

::

    curl -X GET "https://www.ebi.ac.uk/metagenomics/api/latest/studies?page_size=100"


Navigation through pages:

.. highlight:: json

::

    {
      "links": {
        "first": "https://www.ebi.ac.uk/metagenomics/api/latest/studies?page=1",
        "last": "https://www.ebi.ac.uk/metagenomics/api/latest/studies?page=63",
        "next": "https://www.ebi.ac.uk/metagenomics/api/latest/studies?page=26",
        "prev": "https://www.ebi.ac.uk/metagenomics/api/latest/studies?page=24"
      },
      "data": [ ],
      "meta": {
        "pagination": {
          "page": 25,
          "pages": 63,
          "count": 1255
        }
      }
    }


Parameters
^^^^^^^^^^

Lists of resources can be filtered and sorted by selected parameters, allowing
the construction of more complex queries. For instance, in order to retrieve
oceanographic :term:`samples<sample>` from :term:`metagenomic`
:term:`studies<study>` taken at temperature less than 10C, the following query
could be constructed https://www.ebi.ac.uk/metagenomics/api/latest/biomes/root:Environmental:Aquatic:Marine/samples?experiment_type=metagenomic&metadata_key=temperature&metadata_value_lte=10&ordering=accession:

.. highlight:: bash

::

    curl -X GET "https://www.ebi.ac.uk/metagenomics/api/latest/biomes/root:Environmental:Aquatic:Marine/samples?experiment_type=metagenomic&metadata_key=temperature&metadata_value_lte=10&ordering=accession"

The provision of such complex queries allows metadata to be combined with
annotation for powerful data analysis and visualisation.


Customising queries
^^^^^^^^^^^^^^^^^^^

The API response distinguishes between attributes and relationships,
allowing customisation of the response by passing fields or including
relations as parameters in the initial query.

.. highlight:: bash

For example::

    curl -X GET "https://www.ebi.ac.uk/metagenomics/api/latest/studies/ERP005831?include=samples&fields[studies]=accession,study_name,biomes,samples&fields[samples]=accession,longitude,latitude,biome"


.. highlight:: json

::

  {
    "data": {
      "type": "studies",
      "id": "ERP005831",
      "attributes": {
        "accession": "ERP005831",
        "study-name": "Stable isotope probing/metagenomics of terrestrial dimethylsulfide degrading microorganisms"
      },
      "relationships": {
        "biomes": {
            "links": {
                "related": "https://www.ebi.ac.uk/metagenomics/api/v0.3/studies/ERP005831/biomes"
            },
          "data": [
            {
              "type": "biomes",
              "id": "root:Environmental:Aquatic:Freshwater:Lentic:Sediment",
              "links": {
                "self": "https://www.ebi.ac.uk/metagenomics/api/v0.3/biomes/root:Environmental:Aquatic:Freshwater:Lentic:Sediment"
              }
            },
            {
              "type": "biomes",
              "id": "root:Environmental:Terrestrial:Soil:Loam:Agricultural",
              "links": {
                "self": "https://www.ebi.ac.uk/metagenomics/api/v0.3/biomes/root:Environmental:Terrestrial:Soil:Loam:Agricultural"
              }
            }
          ],
          "meta": {
            "count": 2
          }
        },
        "samples": {
          "links": {
            "related": "https://www.ebi.ac.uk/metagenomics/api/v0.3/studies/ERP005831/samples"
          }
        }
      },
      "links": {
          "self": "https://www.ebi.ac.uk/metagenomics/api/v0.3/studies/ERP005831"
      }
    },
    "included": [
      {
        "type": "samples",
        "id": "ERS456668",
        "attributes": {
          "accession": "ERS456668",
          "longitude": -1.56,
          "latitude": 52.38
        },
        "relationships": {
          "biome": {
            "links": {
              "related": "https://www.ebi.ac.uk/metagenomics/api/v0.3/biomes/root:Environmental:Aquatic:Freshwater:Lentic:Sediment"
            },
            "data": {
              "type": "biomes",
              "id": "root:Environmental:Aquatic:Freshwater:Lentic:Sediment"
            }
          }
          },
          "links": {
            "self": "https://www.ebi.ac.uk/metagenomics/api/v0.3/samples/ERS456668"
          }
        },
        {
          "type": "samples",
          "id": "ERS456669",
          "attributes": {
            "accession": "ERS456669",
            "longitude": -1.61,
            "latitude": 52.19
          },
          "relationships": {
            "biome": {
              "links": {
                "related": "https://www.ebi.ac.uk/metagenomics/api/v0.3/biomes/root:Environmental:Terrestrial:Soil:Loam:Agricultural"
              },
              "data": {
                "type": "biomes",
                "id": "root:Environmental:Terrestrial:Soil:Loam:Agricultural"
              }
            }
          },
          "links": {
            "self": "https://www.ebi.ac.uk/metagenomics/api/v0.3/samples/ERS456669"
          }
        }
    ]
  }


Errors
^^^^^^

There are three possible types of client errors on API calls:

* 200 Successful.
* 400 Bad requests.
* 404 Not found.
* 403 Authentication failed.
* 500 Server error.

Cross Origin Resource Sharing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The API supports Cross Origin Resource Sharing (CORS) for AJAX requests from any origin.


--------
Examples
--------

Hands-on tutorial of basic Python API client scripts are available on https://github.com/EBI-Metagenomics/emgapi-examples/blob/master/emgapi/examples/notebook/answers/ANSWER_examples.ipynb


-------------------------
Interactive documentation
-------------------------

We have utilised an interactive documentation framework (Swagger UI) to visualise and simplify interaction with the API’s resources via an HTML interface. Detailed explanations of the purpose of all resources, along with many examples, are provided to guide end-users.

Documentation on how to use the endpoints is available at https://www.ebi.ac.uk/metagenomics/api/docs/.
